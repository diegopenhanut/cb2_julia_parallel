MAPA SEMÂNTICO ISOMÓRFICO DE VARIAÇÕES GENÉTICAS EM VCFs (*variant call format*)
====================================================================================

Emanuel Diego S Penha
---------------------

Orientadora: Diana Magalhães de Oliveira
----------------------------------------



**Introdução**
==============


DNA
===

Dna, genótipo, fenótipo

Saúde e doença

Cada dia mais barato

-   Por que não sequenciar?


Processamento
=============

Série de passos

VCF (variant call format) como produto final

-   Variações encontradas para uma ou mais amostras

Anotações


Dados externos
==============

Uniprot

Uniprot Knowledge Base

-   Swissprot – anotações manuais
-   TrEMBL - anotações automáticas

EBI/NCBI


Linked Data
===========

Dados estruturados

Interligados

-   Não necessariamente por indices e chaves

Consultas Semânticas


Open Linked Data
================
falta figura aqui

5 estrelas de Tim Benners-Lee
=============================

★ make your stuff available on the Web (whatever format) under an open license
------------------------------------------------------------------------------

★★ make it available as structured data (e.g., Excel instead of image scan of a table)
--------------------------------------------------------------------------------------

★★★ use non-proprietary formats (e.g., CSV instead of Excel)
------------------------------------------------------------

★★★★ use URIs to denote things, so that people can point at your stuff
----------------------------------------------------------------------

★★★★★ link your data to other data to provide context
-----------------------------------------------------


RDF
===

Resource Description Framework

Padrão para modelagem de dados para web semântica

Definido pela W3C

Triplas e comunicão verbal

-   Sujeito, verbo, objeto

Uso de URI – Uniform Resource Identifier


Formatos para RDF - XML
=======================

\<rdf:RDF
---------

xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns\#"
--------------------------------------------------------

xmlns:dc="http://purl.org/dc/elements/1.1/"\>
---------------------------------------------

\<rdf:Description rdf:about="http://en.wikipedia.org/wiki/Tony\_Benn"\>
-----------------------------------------------------------------------

\<dc:title\>Tony Benn\</dc:title\>
----------------------------------

\<dc:publisher\>Wikipedia\</dc:publisher\>
------------------------------------------

\</rdf:Description\>
--------------------

\</rdf:RDF\>
------------


Formatos para RDF – N3
======================

@prefix dc: \<http://purl.org/dc/elements/1.1/\>.
-------------------------------------------------

\<http://en.wikipedia.org/wiki/Tony\_Benn\>
-------------------------------------------

dc:title "Tony Benn";
---------------------

dc:publisher "Wikipedia".
-------------------------


Formatos para RDF – Turtle
==========================

@prefix rdf: \<http://www.w3.org/1999/02/22-rdf-syntax-ns\#\> .
---------------------------------------------------------------

@prefix dc: \<http://purl.org/dc/elements/1.1/\> .
--------------------------------------------------

@prefix ex: \<http://example.org/stuff/1.0/\> .
-----------------------------------------------

\<http://www.w3.org/TR/rdf-syntax-grammar\>
-------------------------------------------

dc:title "RDF/XML Syntax Specification (Revised)" ;
---------------------------------------------------

ex:editor [
-----------

ex:fullname "Dave Beckett";
---------------------------

ex:homePage \<http://purl.org/net/dajobe/\>
-------------------------------------------

] .
---


Formatos para RDF - N-triples
=============================

\<http://www.w3.org/TR/rdf-syntax-grammar\> \<http://purl.org/dc/elements/1.1/title\> "RDF/XML Syntax Specification (Revised)" .
--------------------------------------------------------------------------------------------------------------------------------

\<http://www.w3.org/TR/rdf-syntax-grammar\> \<http://example.org/stuff/1.0/editor\> \_:bnode .
----------------------------------------------------------------------------------------------

\_:bnode \<http://example.org/stuff/1.0/fullname\> "Dave Beckett" .
-------------------------------------------------------------------

\_:bnode \<http://example.org/stuff/1.0/homePage\> \<http://purl.org/net/dajobe/\> .
------------------------------------------------------------------------------------


SPARQL
======


Sparqlgraph
===========


Justificativa
=============

Médico, pacientes, bioinformata…

-   A quem interessa a informação?

Agulha em palheiro?

Proteção aos dados do paciente

Objetivos
=========

Geral

-   Identificar mapa isomorfo entre VCF e RDF, permitindo transformar um
    arquivo local em um objeto para consultas em RDF.

Específicos

-   Identificar um modelo semântico neutro, em relação a domínio, que
    permita inferência de triplas. 
-   Desenvolver estrutura em nuvem (*cloud*) para expor arquivos em
    formato VCF como SPARQL endpoints.

**Revisão de Literatura**
=========================

Histórico do Projeto Genoma Humano
==================================

Publico vs Privado

-   Venter vs Watson

Diferenças de tecnologia

Em 2001 anunciam primeiro rascunho

-   Nature e science

Breve Histórico do Sequenciamento do DNA
========================================

Da nucleina em 1896 por Friedrich Miescher até a dupla Hélice por:

-   Maurice Wilkins
-   Rosalind Franklin & Raymond Gosling
-   Watson & Crick

Primeiro sequenciamento em 1972 (Jou eta al)

Primeiro genoma em 1977 (Sanger et al)

-   Ainda hoje tido como padrão

Sequenciamento de Nova Geração
==============================

Reads mais curtas, com maior quantidade

-   Maior volume de dados em menos tempo

FastQ -\> BAM/SAM -\> VCFs

Pipeline para gerar o VCF
=========================

Proxima geração
===============

Ion-torrent

-   Rápido sequenciamento com baixo custo
-   Dificultades de diferenciar variações no número de cópias(CNV)
-   Pequena escala

Nanopore

-   MinION (tamanho de um pendrive)
-   Mede alteração em corrente elétriac pela passagem de nucleotídeos em
    nanoporos.

Nutrigenômica e sua relação com os VCFs
=======================================

-   genótipo; expressão gênica; epigenótipo vs variável nutritional
-   Conhecimento de mutação pode alterar comportamento
-   VCFs são a maneira de armazenar informações sobre mutações
-   Então são base para o primeiro tipo de estudo

Linked Data e RDF
=================

**Metodologia**
===============

Condições e autorizações laboratoriais
======================================

-   O trabalho desenvolvido nesta dissertação, a ser defendida dentro do
    Curso de Mestrado Acadêmico em Nutrição e Saúde (CMANS) da UECE em
    Fortaleza, Ceará, Brasil, foi executado na Divisão de Informática do
    Departamento de Patologia na University of Alabama at Birmingham
    (UAB), nos Estados Unidos da América, como parte de treinamento
    técnico-científico realizado na forma de Mestrado-Sanduíche naquela
    instituição Norte-Americana, sob supervisão do Prof. Dr. Jonas S.
    Almeida.

Materiais e amostras de Estudo
==============================

The Cancer genome Atlas

-   VCFs

DBsnp

-   Anotação do VCF;

Sequencias e dados biológicos
=============================

Softwares e Recursos Computacionais
===================================

JavaScript

-   Jquery
-   Datatables
-   Meteor / Noje.js

R

-   Pacote no github

Node.js Meteor

Mostrar figuras com exemplos ou links
=====================================

Base para mapeamento e uso de Ids
=================================

Rede de relações intrincada

Cabeçalho vs corpo, corpo vs corpo

Uso de Ids como representação de pontos de intersecção entre essas
relações

Assim é possível respeitar essas relações

-   Vários arquivos ao mesmo tempo
-   Várias mutações ao mesmo tempo

**Resultados**
==============

Mapa Isomorfico
===============

\

### Notes:

Substituir figura, usar algo em d3.js

URIs
====

<http://diegopenhanut.github.io/vcf-resources/v4_2/>

URI definidas usando github pages

Python script é usado para gerar as páginas e estrutura de diretórios

-   <https://github.com/diegopenhanut/vcf-resources/blob/gh-pages/v4_2/createPages.py>
-   <https://github.com/diegopenhanut/vcf-resources/blob/gh-pages/v4_2/structure.csv>

Publicações vinculadas
======================

Poster
======

PATHOLOGY TRAINEE RESEARCH DAY, UAB

-   ISOMORPHIC SEMANTIC MAPPING OF GENOMIC VARIATION CALLING FORMAT

Manuscript
==========

VCFR

-   sobre o modelo de dados em si.
-   Isomorphic semantic mapping of genomic variation calling format
    (VCF)
-   Application Notes, Oxford Bioinformátics.

Conclusão
=========

-   O presente estudo identificou um mapa isomórfico entre o VCF e o
    RDF, com um modelo neutro de domínio. Foi disponibilizado um sparql
    endpoint \<<http://diegopenhanut.me:8080/lodestar/sparql>\> para
    testes com os VCFs convertidos.
-   O modelo desenvolvido, chamado de VCFr junto as suas ferramentas
    para gerá-lo, mostrou-se versátil, por dar uma granularidade e uma
    capacidade de consulta que um arquivo de texto comum não permite.

\

### Notes:

Ver lodestar e instalar virtuoso

Conclusão
=========

muitos identificadores únicos

-   aumento do tamanho dos arquivos por volta de 5 vezes

Em testes, arquivos 160mb não são problema

Conclusão
=========

-   Desenvolvido modelo de dados
-   E algumas aplicações menores que oferecem a possibilidade, ao
    paciente e ao médico, de se obter dados diretamente do VCF e
    ligá-los a diferentes bases de dados.

Obrigado
========
