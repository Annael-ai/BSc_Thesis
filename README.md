Breast Cancer Knowledge Graph

This project builds a Neo4j knowledge graph from the internship.csv dataset, integrating clinical, mutation, and gene expression data for 1904 breast cancer patients.
Dataset
internship.csv includes:
Clinical data (e.g., age, tumor stage, cancer type)
Gene mutations (e.g., tp53_mut, cdh1_mut)
Gene expression values (e.g., aurka, brca1)
Graph Structure
Nodes:
:Patient – includes full clinical metadata
:GeneMutation – one per mutation gene 
:ExpressionGene – one per expression gene
Relationships:
(:Patient)-[:HAS_MUTATION {mutation_location}]->(:GeneMutation)
(:Patient)-[:EXPRESSES {expression_value}]->(:ExpressionGene)
(:GeneMutation)-[:IS_SAME_GENE]->(:ExpressionGene)
Features
Complete patient node creation with all clinical fields
Filtered import of non-zero, non-null mutation and expression values
Triple-negative and basal-like phenotype tagging
Grouping patients by subtype combinations (e.g., TNBC + basal-like)
Expression percentile and bracket analysis (e.g., AURKA)
Mutation frequency analysis (e.g., TP53, CDH1)
Usage
All logic is implemented using Cypher queries. Data is loaded via LOAD CSV WITH HEADERS from internship.csv. Queries are optimized for Neo4j Browser and Neo4j Bloom.
