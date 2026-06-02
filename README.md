# PDB Reader and Hetero-Compound Interaction Analyzer

## Overview

This project implements an object-oriented PDB (Protein Data Bank) file reader for structural bioinformatics applications. The program parses PDB files, extracts atomic coordinates for protein and hetero (non-protein) atoms, and provides methods for querying structural information and computing atomic interactions.

The project also identifies the hetero-compound with the highest average atomic interaction score based on a distance cutoff of 5 Å.

---

## Features

### PDB Parsing

* Reads and parses PDB structure files.
* Extracts:

  * Protein atoms (`ATOM` records)
  * Hetero atoms (`HETATM` records)
  * Residue information
  * Atomic coordinates

### Available Methods

#### `listAtoms(residueNumber)`

Returns a list of all atoms belonging to the specified residue.

**Example**

```python
reader.listAtoms(25)
```

#### `coordAtom(residueNumber, atomName)`

Returns the Cartesian coordinates of a specified atom.

**Example**

```python
reader.coordAtom(25, "CA")
```

#### `hetero()`

Returns all hetero-compound identifiers present in the structure.

**Example**

```python
reader.hetero()
```

#### `distanceAtoms(res1, atom1, res2, atom2)`

Computes the Euclidean distance between two atoms.

**Example**

```python
reader.distanceAtoms(25, "CA", 30, "CB")
```

---

## Interaction Analysis

Two atoms are considered interacting if:

```text
Distance ≤ 5 Å
```

For each hetero-compound:

1. Count the number of interacting atoms between the hetero-compound and the surrounding structure.
2. Determine the total number of atoms in the hetero-compound.
3. Compute the average interaction score:

```text
Average Interaction Score =
(Number of Interacting Atoms) /
(Number of Atoms in Hetero-Compound)
```

The hetero-compound with the highest average interaction score is reported as the most interacting hetero-compound.

---

## Project Structure

```text
.
├── pdb_reader.ipynb
├── sample.pdb
-── README.md
```


---

## Algorithms Used

### Distance Calculation

The Euclidean distance between two atoms is calculated using:

```text
d = √[(x₂ − x₁)² + (y₂ − y₁)² + (z₂ − z₁)²]
```

### Interaction Detection

```text
if distance ≤ 5 Å:
    atoms are interacting
```

---

## Applications

* Protein structure analysis
* Ligand interaction studies
* Structural bioinformatics
* Drug-binding site investigation
* Molecular contact analysis

---

## Author

Developed as part of a Structural Bioinformatics project focused on PDB parsing, atomic coordinate extraction, and hetero-compound interaction analysis.
