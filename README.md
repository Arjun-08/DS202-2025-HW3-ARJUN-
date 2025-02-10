# Longest Repeat in Genomic Sequences

## **Introduction**
Repetitive DNA plays an important functional and evolutionary role in genomes. However, it also makes computational problems such as genome assembly challenging. This project identifies the **longest repeated substring** in a given input text using a **suffix array (SA)** and **longest common prefix (LCP) array**.

Given an input genomic sequence (e.g., human chromosome Y), the algorithm computes:
1. The **length** of the longest repeat.
2. The **starting positions** of this repeat in the text.
3. The **execution time** for suffix array (SA) and LCP computation.
4. The **peak memory usage** of the program.

## **Assumptions**
- The input is a **FASTA** file containing a single sequence.
- The sequence consists of uppercase **DNA characters (A, T, C, G, N)**.
- Indices in the output are **zero-based**.

---

## **Prerequisites**
The project requires Python 3 and the `pydivsufsort` library for suffix array computation.

- **Python Version**: 3.x
- **Library Used**: [`pydivsufsort`](https://pypi.org/project/pydivsufsort/)

### **Installing Dependencies**
Run the following command to install the required library:
```sh
pip install pydivsufsort
