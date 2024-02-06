# AlphaFold Bulk Downloader Documentation

The `alphafoldbulk.py` script is designed to automate the downloading of PDB (Protein Data Bank) files from the AlphaFold Protein Structure Database given a list of protein sequences. It fetches the PDB URL for the latest model of each sequence and downloads the corresponding PDB file.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
  - [Command Line Arguments](#command-line-arguments)
  - [Input File Format](#input-file-format)
- [Functions](#functions)
  - [get_pdb_url](#get_pdb_url)
  - [download_pdb](#download_pdb)
- [Examples](#examples)
- [Error Handling](#error-handling)

## Installation

Before running the script, ensure you have Python installed on your machine. The script requires the `requests` library, which can be installed using the following command:

```bash
pip install requests
```

## Usage

The script is run from the command line with two arguments: the path to the file containing the protein sequences and the path to the output directory where the PDB files will be saved.

### Command Line Arguments

```plaintext
python alphafoldbulk.py <sequences_file> <output_dir>
```

- `<sequences_file>`: A text file containing the protein sequences, one per line. Optionally, each line can contain a label followed by a colon and then the sequence.
- `<output_dir>`: The directory where the downloaded PDB files should be saved.

### Input File Format

The input file containing protein sequences should have one sequence per line. If you wish to include identifiers or labels for each sequence, format each line as follows:

```
<label>:<sequence>
```

For example:

```
Protein1:MFVFLVLLPLVSSQCVNLTTRTQLPPAYTNSFTRGVYYPDKVFRSSVLHSTQDLFLPFFSNVTWFHAPT
Protein2:MFADRWLFSTNHKDIGTLYLIFGAWAGMVGTALSLLIRAELGQPGALLGDDQIYNVIVTAHAFVMIFFM
```

If no label is provided, the sequence itself will be used as the identifier for the output file.

## Functions

### `get_pdb_url`

Fetches the PDB URL for a given protein sequence.

#### Arguments:

- `sequence`: A string representing the protein sequence.

#### Returns:

- A string containing the URL to the PDB file, or `None` if no URL was found.

### `download_pdb`

Downloads a PDB file from a specified URL to an output file.

#### Arguments:

- `pdb_url`: The URL from which to download the PDB file.
- `output_file`: The file path where the PDB file should be saved.

## Examples

To download PDB files using the `alphafoldbulk.py` script, follow these steps:

1. Create a text file with your protein sequences, one sequence per line.
2. Choose or create an output directory to save the downloaded PDB files.
3. Run the script using the command line with the path to your sequences file and output directory:

```bash
python alphafoldbulk.py sequences.txt /path/to/output_directory
```

## Error Handling

The script will print error messages in the following cases:

- Incorrect usage: If an incorrect number of arguments is supplied, the script will print a usage message.
- Failed PDB URL retrieval: If the script cannot retrieve a PDB URL for a given sequence, it will print a message indicating the failure.
- Failed download: If the script cannot download the PDB file from the provided URL, it will print a message indicating the failure.

In all cases, the script will continue processing the remaining sequences.