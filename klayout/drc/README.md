# DRC Documentation

Explains how to use the runset.

## Folder Structure

```text
📁drc
 ┣ 📁testing
 ┣ 📁rule_decks
 ┣ 📜README.md
 ┗ 📜run_drc.py
 ```

## Rule Deck Usage
The `run_drc.py` script takes a gds file to run DRC rule decks of GF180 technology with switches to select subsets of all checks. 

### Requirements
Please make sure to use the latest Klayout setup at your side. To install klayout, please refer to documentation at [klayout build](https://www.klayout.de/build.html).

Also, please make sure to install the required python packages at `requirements.txt` by using
```bash
pip install -r requirements.txt
```

### Metal Stack Options
We have a list of metal stack options which corresponds to the following:
- **Option A** : combined options of metal_level=3, mim_option=A, metal_top=30K, poly_res=1K, and mim_cap=2
- **Option B** : combined options of metal_level=4, mim_option=B, metal_top=11K, poly_res=1K, and mim_cap=2
- **Option C** : combined options of metal_level=5, mim_option=B, metal_top=9K,  poly_res=1K, and mim_cap=2

### Usage

```bash
    run_drc.py (--help| -h)
    run_drc.py (--path=<file_path>) (--gf180mcu=<combined_options>) [--topcell=<topcell_name>] [--thr=<thr>] [--run_mode=<run_mode>] [--no_feol] [--no_beol] [--connectivity] [--density] [--density_only] [--antenna] [--antenna_only] [--no_offgrid]
```

Example:

```bash
    python3 run_drc.py --path=testing/switch_checking/simple_por.gds.gz --thr=16 --run_mode=flat --gf180mcu=A --antenna --no_offgrid
```

### Options

- `--help -h`                           Print this help message.

- `--path=<file_path>`                  The input GDS file path.

- `--gf180mcu=<combined_options>`       Select combined options of metal_top, mim_option, and metal_level. Allowed values (A, B, C).
  - gf180mcu=A: Select  metal_top=30K  mim_option=A  metal_level=3LM
  - gf180mcu=B: Select  metal_top=11K  mim_option=B  metal_level=4LM
  - gf180mcu=C: Select  metal_top=9K   mim_option=B  metal_level=5LM

- `--topcell=<topcell_name>`            Topcell name to use.

- `--thr=<thr>`                         The number of threads used in run.

- `--run_mode=<run_mode>`               Select klayout mode Allowed modes (flat , deep, tiling). [default: flat]

- `--no_feol`                           Turn off FEOL rules from running.

- `--no_beol`                           Turn off BEOL rules from running.

- `--connectivity`                      Turn on connectivity rules.

- `--density`                           Turn on Density rules.

- `--density_only`                      Turn on Density rules only.

- `--antenna`                           Turn on Antenna checks.

- `--antenna_only`                      Turn on Antenna checks only.

- `--no_offgrid`                        Turn off OFFGRID checking rules.

### **DRC Outputs**

Results will appear at the end of the run logs.

The result is a database file (`<your_design_name>.lyrdb`) of all violations in the same directoy of your design. you could view it on your file using klayout.
