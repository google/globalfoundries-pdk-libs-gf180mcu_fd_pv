# Globalfoundries 180nm MCU DRC Tests


## Folder Structure

```text
π testcases
 β£ πREADME.md                       This file to document the unit tests.
 β£ π unit                           Contains the unit test structures per rule.
    β£ π<table_name>.gds                Test cases per table.
    β£ π<table_name>.svg                SVG file per table.
    β£ π<table_name>.yaml               yaml file contains switches per table. [if required]
 β£ π switch_checking                Contains a small test case to be used for testing the DRC switches.
 β£ π torture                        Contains a few large test cases to test the performance of the rule deck. 

 ```
 