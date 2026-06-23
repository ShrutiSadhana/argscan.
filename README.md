# argscan.
ARGScan screens genomic sequences against a curated resistance gene database using k-mer indexing — detecting antibiotic resistance markers in seconds.
Yes, this is the complete backend. Here's every file and what it contains:

**5 core modules:**

- `parser.py` — `FastaRecord` dataclass, `parse_fasta()`, `get_sequences()`
- `kmer.py` — `generate_kmers()`, `build_kmer_index()`
- `database.py` — `ResistanceGene` dataclass, `load_database()`, `index_by_name()`, `index_by_family()`
- `detector.py` — `DetectionHit` dataclass, `compute_score()`, `detect()`
- `cli.py` — `parse_args()`, `read_query_sequence()`, `format_results()`, `main()`

**3 test files:**

- `test_kmer.py` — 6 unit tests for k-mer generation and indexing
- `test_database.py` — 5 tests for database loading and indexing
- `test_detector.py` — 5 integration tests for detection logic

**2 data files:**

- `resistance_genes.fasta` — 3 reference genes (tetA, blaTEM-1, aacA4)
- `query.fasta` — sample query sequence

**2 config files:**

- `pyproject.toml` — makes it pip-installable as `arg-detector`
- `run.bat` — one-click Windows launcher

The only thing not production-ready is the **database** — the 3 bundled genes are for demo/testing. For real research, replace `resistance_genes.fasta` with a download from [CARD](https://card.mcmaster.ca/download) or [ResFinder](https://cge.food.dtu.dk/services/ResFinder/). The code handles any FASTA database of any size with no changes.
