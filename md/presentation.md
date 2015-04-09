![UAB_logo](figuras/uab_logo.png)

### Parallel processing in Julia using Grid Engine
-----
###### Emanuel Diego S Penha
###### Research Scholar
http://goo.gl/tkSwLg


Note: Bom dia!



Introduction
============
Julia is a new-high level computer language built for technical computing with performance in mind. Julia processes can create tasks that utilize large computational resource, these can be ran using clusters. 


Clusters are a massive network of computers that can be viewed as a single system. To best harness the power of such machines, code is typically ran in parallel.


While clusters can be viewed as a single system, they required a way to manage processes and processors. One such tool is Grid Engine. 


Grid Engine is a program for executing batch jobs on linux clusters. The main idea is to provide a way to schedule big and small jobs and maintain the cluster in a optimal state.The cluster will use available memory and processors as parameters to determine in what order jobs run. 


The main objective of this discussion is to describe how one can use another other than Julia and the queuing system of Grid Engine to complete tasks, particularly int the field of bioinformatics.
Note: You need to say that are different types of parallel processing, The julia way is one-way messages. But this is off topic. We are not talking about that today



Binary at 
=========
```
/home/penhaeds/bin/julia-cb9bcae93a/bin/julia
```
Note: Give time to people find your binary



Online at
=========
[https://www.juliabox.org/](https://www.juliabox.org/)
Note: Give time to people find the site and set up accounts



Basic Communication
===================
```julia
$ ./julia -p 2

julia> r = remotecall(2, rand, 2, 2)
RemoteRef(2,1,5)

julia> fetch(r)
2x2 Float64 Array:
 0.60401   0.501111
 0.174572  0.157411

julia> s = @spawnat 2 1 .+ fetch(r)
RemoteRef(2,1,7)

julia> fetch(s)
2x2 Float64 Array:
 1.60401  1.50111
 1.17457  1.15741
 ```
 [Click here for a more complete example](ipython_ijulia_examples/cb2_basic_parallel_communication.html)
Note: Show IJulia and code running


dataframes
==========
```julia
julia> using(DataFrames)
julia> df = DataFrame(Origin = ["a","b","c","d","a","d"], 
	Target = ["j", "f", "g", "h", "i", "j"])
julia> df[:Target]
julia> p = randperm(length(df[:Target]))
julia> df[:Target]=df[:Target][p]
julia> df
```
Note: Explain what you are going to do. Randomization of a column in
one dataframe. Talk about rewiring of networks emidio told.


```julia
function randNdCol(mytable)
	p=randperm(length(mytable[2]))
	mytable[2]=mytable[2][p]
	return mytable
	end
```
Note: This is a function to reorder.
Talk about the simgle thread, and possibilities to have a 
distribuition of this data


```julia
randNdCol(df)
```
Note: This is a the calling of the function



Load data/functions to all processes
====================================
```julia
julia> require("myfile")
@everywhere id = myid()
```
Note: talk about each process needs to have a copy or chunk of the data
to work on.
Maybe talk a little bit about macros.


data, functions and processes
=============================================
```julia
addprocs(5)
@everywhere using(DataFrames)
@everywhere df = DataFrame(Origin = ["a","b","c","d","a","d"], 
Target = ["j", "f", "g", "h", "i", "j"])
@everywhere function randNdCol(mytable)
	p=randperm(length(mytable[2]))
	mytable[2]=mytable[2][p]
	return mytable
	end
newDf = @spawn randNdCol(df)
fetch(newDf)
```
Note: One can use a loop to dispatch the jobs,
parallelism is limited here


```julia
addprocs(5)

@everywhere using(DataFrames)

@everywhere df = DataFrame(Origin = ["a","b","c","d","a","d"], 
Target = ["j", "f", "g", "h", "i", "j"])

@everywhere function randNdCol(mytable)
	p=randperm(length(mytable[2]))
	mytable[2]=mytable[2][p]
	return mytable
	end

M = [df for i=1:100]
pmap(randNdCol, M)
```
[take a look at the output](ipython_ijulia_examples/cb2_julia_parallel_dataframe.html)



Using ClusterManagers
=====================
```julia
julia> Pkg.update()
julia> Pkg.add("ClusterManagers")
julia> using ClusterManagers
julia> ClusterManagers.addprocs_sge(5)

job id is 512301, waiting for job to start .................
5-element Array{Any,1}:
 2
 3
 4
 5
 6
```
Note:Each process has an associated identifier.
The process providing the interactive julia prompt always has an id
equal to 1, as would the julia process running the driver script in the
example above.
The processes used by default for parallel operations are referred to as
workers. When there is only one process, process 1 is considered a
worker.
Otherwise, workers are considered to be all processes other than
process 1


The Diference now is 
====================
```Julia
ClusterManagers.addprocs_sge(5)
```
instead of 
```julia
addprocs(5)
```


New code 
========
```julia
ClusterManagers.addprocs_sge(5)
@everywhere using(DataFrames)
@everywhere df = DataFrame(Origin = ["a","b","c","d","a","d"], 
Target = ["j", "f", "g", "h", "i", "j"])
@everywhere function randNdCol(mytable)
    p=randperm(length(mytable[2]))
    mytable[2]=mytable[2][p]
    return mytable
    end

newDf=[]

M = [df for i=1:10]
pmap(randNdCol, M)
```



Take a look at the workers on sge
=================================
```
qstat
```



Take a look at the workers on julia
===================================
```julia
workers()
```



Remove workers from julia
==============
```julia
rmprocs(workers());
```
Note: As malay said before, do not install if you don't know how to unistall



Remove workers from sge
==============
```shell
qdel -u username
```
Note: Remember that the jobs will die if not used.
This happened to me.



Nodes
=====
```julia
julia> @parallel for i=1:5
       run(`hostname`)
       end

julia>  From worker 2:  alto
        From worker 5:  alto
        From worker 4:  alto
        From worker 6:  alto
        From worker 3:  alto
```
Note:
this will be hidden by default



Reduce Example
==============
```julia
nheads = @parallel (+) for i=1:200000000
randbool()
end
```
Note: this is a kind of mapping
One uses (+) in the middle to add a reduce function



### Thank you!
-----
penhaeds@uab.edu




