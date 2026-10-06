# statistical-analysis-project

## Project description

I built one Jupyter notebook, `analysis.ipynb`, that asks whether the share of invoices paid late
by large UK companies was lower in 2023 to 2024 than in 2018 to 2019, for the companies that
reported in both periods. The data is the GOV.UK payment practices reports, which large companies
must publish at least twice a year. The notebook checks, describes and screens the data, then
draws three visual models, fits one statistical model and runs one hypothesis test.

## Dataset

- Name: Check when large businesses pay their suppliers, the GOV.UK payment practices reports
  (all published reports)
- Source: <https://www.gov.uk/check-when-businesses-pay-invoices>
- Licence: Open Government Licence v3.0,
  <https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/>, as stated on the
  service page

[TO WRITE: the source category note]

[TO WRITE: the regime note]

Contains public sector information licensed under the Open Government Licence v3.0.

## Data

- Export: <https://check-payment-practices.service.gov.uk/export/csv/>
- Downloaded: 6 Oct 2026
- File: `all_published_reports_20261006.csv`
- Size: 103,043,357 bytes (103 MB)
- SHA-256: `f9f2552222190b9c5f1ca145cdc1771ac88ba81c38fcfef49fe64c3b696db535`

The CSV is not in this repository because at 103 MB it is large raw data, which does not belong
in Git history, so it is supplied in the submission zip instead.

To place it, copy `all_published_reports_20261006.csv` from the submission zip into the
repository folder, beside `analysis.ipynb`, and keep its name. The export link above gives every
report published up to the day you use it, so a new download will be a different file. The
notebook's first check compares the file's SHA-256 with the one above and stops if they differ.

## How to run

You need Git and **Python 3.12 or newer**, because the pinned versions of numpy and scipy will not
install on older versions. The notebook was run with Python 3.12.3. Check yours with
`python3 --version` (on Windows, `py --version`).

1. Clone this repository and move into its folder:

   ```bash
   git clone https://github.com/PaddyGilliland1/statistical-analysis-project.git
   cd statistical-analysis-project
   ```

2. Create and activate a virtual environment:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

   On Windows, create and activate it in PowerShell with:

   ```powershell
   py -3.12 -m venv .venv
   .venv\Scripts\Activate.ps1
   ```

3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Copy `all_published_reports_20261006.csv` from the submission zip into the repository folder,
   beside the notebook, as the Data section above describes.

5. Open the notebook, then restart the kernel and run all cells:

   ```bash
   jupyter notebook analysis.ipynb
   ```

   The notebook reads the CSV from its own folder, so start Jupyter from the repository folder.

## How requirements.txt was created

The notebook was run top to bottom in a fresh virtual environment, and the file was then written
from that environment with:

```bash
pip freeze > requirements.txt
```

## Notes on the brief

[TO WRITE: the notes on contradictions C1, C2, C3, C12 and C14]

## Reflections

[TO WRITE: one ### heading per reflection question in the brief, each answered in your own words.]
