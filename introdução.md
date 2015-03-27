Introdução
==========


DNA
===

- Dna, genótipo, fenótipo
- Saúde e doença
- Cada dia mais barato
   - Por que não sequenciar?


Processamento
=============

- Série de passos
- VCF (variant call format) como produto final
  - Variações encontradas para uma ou mais amostras
- Anotações


Dados externos
==============

- Uniprot
- Uniprot Knowledge Base
  - Swissprot – anotações manuais
  - TrEMBL - anotações automáticas
- EBI/NCBI


Linked Data
===========

- Dados estruturados
- Interligados
  - Não necessariamente por indices e chaves
- Consultas Semânticas



Open Linked Data
================



5 estrelas de Tim Benners-Lee
=============================

★ make your stuff available on the Web (whatever format) under an open license


★★ make it available as structured data (e.g., Excel instead of image scan of a table)


★★★ use non-proprietary formats (e.g., CSV instead of Excel)


★★★★ use URIs to denote things, so that people can point at your stuff


★★★★★ link your data to other data to provide context



RDF
===

- Resource Description Framework
- Padrão para modelagem de dados para web semântica
- Definido pela W3C
- Triplas e comunicão verbal
  - Sujeito, verbo, objeto
- Uso de URI – Uniform Resource Identifier



Formatos para RDF

XML
=======================
```
<rdf:RDF
xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
xmlns:dc="http://purl.org/dc/elements/1.1/">
  <rdf:Description rdf:about="http://en.wikipedia.org/wiki/Tony_Benn">
  <dc:title>Tony Benn</dc:title>
  <dc:publisher>Wikipedia<dc:publisher>
</rdf:Description>
</rdf:RDF>

```


Formatos para RDF

N3
======================
```
@prefix dc:<http://purl.org/dc/elements/1.1/>.
<http://en.wikipedia.org/wiki/Tony_Benn>
dc:title "Tony Benn";
dc:publisher "Wikipedia".
```

### Notes:

Verificar se a notação para N3 é essa mesmo. estou achando muito simples


Formatos para RDF

Turtle
==========================
```
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix dc: <http://purl.org/dc/elements/1.1/> .
@prefix ex: <http://example.org/stuff/1.0/> .
<http://www.w3.org/TR/rdf-syntax-grammar>
dc:title "RDF/XML Syntax Specification (Revised)" ;
ex:editor [
ex:fullname "Dave Beckett";
ex:homePage <http://purl.org/net/dajobe/>
] .
```


Formatos para RDF

N-triples
=============================
```{xml}
<http://www.w3.org/TR/rdf-syntax-grammar>
<http://purl.org/dc/elements/1.1/title>
"RDF/XML Syntax Specification (Revised)" .

<http://www.w3.org/TR/rdf-syntax-grammar>
<http://example.org/stuff/1.0/editor>
_:bnode .

_:bnode
<http://example.org/stuff/1.0/fullname>
"Dave Beckett" .
_:bnode
<http://example.org/stuff/1.0/homePage>
<http://purl.org/net/dajobe/> .
```


SPARQL
======



Sparqlgraph
===========
