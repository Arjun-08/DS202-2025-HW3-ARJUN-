# **Longest Repeat in Genomic Sequences**

## **Introduction**
Repetitive DNA plays an important functional and evolutionary role in genomes. However, it also makes computational problems such as genome assembly challenging. This project identifies the **longest repeated substring** in a given input text using a **suffix array (SA)** and **longest common prefix (LCP) array**.

Given an input genomic sequence (e.g., human chromosome Y), the algorithm computes:
1. The **length** of the longest repeat.
2. The **starting positions** of this repeat in the text.
3. The **execution time** for suffix array (SA) and LCP computation.
4. The **peak memory usage** of the program.

---

## **Dataset Information**
- The dataset used in this project is **chromosome Y** of the human genome, downloaded from:  
  🔗 [NCBI Chromosome Y Dataset](https://www.ncbi.nlm.nih.gov/nuccore/CP086569.2)
- The **FASTA file** containing the sequence was uploaded to **Google Colab** and used as the input.

---

## **Assumptions**
- The input is a **FASTA** file containing a single genomic sequence.
- The sequence consists of uppercase **DNA characters (A, T, C, G, N)**.
- Indices in the output are **zero-based**.

---

## **Prerequisites**
This project requires **Python 3** and the `pydivsufsort` library for suffix array computation.

- **Python Version**: 3.x
- **Library Used**: [`pydivsufsort`](https://pypi.org/project/pydivsufsort/)

### **Installing Dependencies**
Run the following command to install the required library:
```sh
pip install pydivsufsort
```

---

## **How to Run the Program**

### **On Google Colab**
1. Open Google Colab and upload your FASTA file (`sequence.fasta`).
2. Mount Google Drive:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
3. Move the FASTA file to Colab’s working directory:
   ```sh
   !cp /content/drive/MyDrive/sequence.fasta /content/
   ```
4. Install the required library:
   ```sh
   !pip install pydivsufsort
   ```
5. Run the Python script:
   ```sh
   !python3 longest_repeat.py /content/sequence.fasta
   ```

### **Executing Locally**
1. Install dependencies:
   ```sh
   pip install pydivsufsort
   ```
2. Run the program with:
   ```sh
   python3 longest_repeat.py sequence.fasta
   ```
3. Alternatively, using a Makefile:
   ```sh
   make run
   ```

---

## **Algorithm Description**
The algorithm follows three key steps:

### **1. Suffix Array Construction (SA(T))**
- Uses `pydivsufsort.divsufsort(text)`, an efficient **O(n log n)** algorithm for suffix array construction.
- Outputs an array where each element represents the starting position of a suffix in sorted order.

### **2. LCP Array Computation (LCP(T))**
- Implements a linear-time **O(n)** algorithm that:
  - Builds a rank array storing suffix positions.
  - Uses a two-pointer technique to compute common prefixes efficiently.
- Each element in the LCP array represents the length of the longest common prefix between two consecutive suffixes in the suffix array.

### **3. Finding the Longest Repeat**
- Finds the maximum value in the LCP array.
- Extracts all occurrences of the longest repeated substring.
- Tracks the starting positions of all occurrences.
- Returns the longest repeat along with its length and positions.

---

## **Code Breakdown**

### **1. `compute_suffix_array(text)`**
Computes the suffix array of `text` using the `pydivsufsort` library.

### **2. `compute_lcp(text, SA)`**
Computes the longest common prefix (LCP) array in **O(n)** time.

### **3. `longest_repeat(text, SA, LCP)`**
Extracts the longest repeated substring, its length, and positions.

### **4. `load_fasta(filename)`**
Reads the FASTA sequence (ignoring headers).

### **5. `main()`**
Reads input, computes SA and LCP, finds the longest repeat, and reports:
- **Length of longest repeat**
- **Positions where it occurs**
- **Execution time**
- **Peak memory usage**

---

## **Results**

Input text length: 62460029 characters

RESULTS:
---------
Length of the longest repeat: 81262
Starting positions of the longest repeat: [58413702, 59261387]
Wall-clock time for SA and LCP construction: 701.606730 seconds
Peak memory usage: 4303592 KB
```

---

## **Performance Complexity**

| Step                        | Algorithm                | Complexity   |
|-----------------------------|--------------------------|-------------|
| Suffix Array (SA) Construction | `divsufsort (O(n log n))` | **O(n log n)** |
| LCP Array Computation       | Kasai Algorithm          | **O(n)**     |
| Finding Longest Repeat      | Linear Scan              | **O(n)**     |
| **Total Complexity**        |                          | **O(n log n)** |

---

## **Measuring Execution Time and Memory Usage**
To measure memory usage in Linux:
```sh
/usr/bin/time -v python3 longest_repeat.py sequence.fasta
```

This command provides detailed execution time and memory usage statistics.

---

## **Conclusion**
This project successfully identifies the **longest repeated substring** in a genomic sequence using **suffix arrays** and **LCP arrays**. The implementation efficiently computes the results in **O(n log n)** time complexity, making it scalable for large genomic sequences.

Future work may include:
- Enhancing performance for extremely large genomes.
- Extending the algorithm to handle multiple sequences.
- Exploring applications in genome assembly and comparative genomics.

**Keywords**: Suffix Array, LCP Array, Genomic Repeats, Sequence Analysis, Computational Biology.
