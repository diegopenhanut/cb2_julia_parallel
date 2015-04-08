![UAB_logo](figuras/uab_logo.png)

### Parallel processing in Julia using Grid Engine
-----
###### Emanuel Diego S Penha
###### Research Scholar



Julia Examples
==============
```{julia}
using Gadfly
using RDatasets
bmiData=dataset ("datasets", "women")
bmiData[:BMI]=1
print(bmiData[:BMI])
print(bmiData)
bmi(w,h)= (w ./ int64([i^2 for i in h]) * 703
print(bmi(154, 72))
print(bmi([154,152], [72,70]))
for row in eachrow (bmiData)
    print(bmi(row[:Weight], row[:Height]))
end
bmi(bmiData[:Weight], bmiData[:Height])
print(bmiData)

```

