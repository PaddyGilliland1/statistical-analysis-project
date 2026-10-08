# statistical-analysis-project

## Project description

I built one Jupyter notebook, `analysis.ipynb`, that asks whether the share of invoices paid late
by large UK companies was lower in 2023 to 2024 than in 2018 to 2019, for the companies that
reported in both periods. The data is the GOV.UK payment practices reports, which a large company
normally publishes for each half of its financial year. The notebook checks, describes and
screens the data, then draws three visual models, fits one statistical model and runs one
hypothesis test. It needs Python 3.12 or newer, because the pinned packages require it, and I
ran it with Python 3.12.3.

## Dataset

- Name: Check when large businesses pay their suppliers, the GOV.UK payment practices reports
  (all published reports)
- Source: <https://www.gov.uk/check-when-businesses-pay-invoices>
- Licence: Open Government Licence v3.0,
  <https://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/>, as stated on the
  service page

The brief lists five kinds of accepted source. This dataset comes from an open government data
portal: GOV.UK's "Check when large businesses pay their suppliers" service
(https://www.gov.uk/check-when-businesses-pay-invoices), whose pages state that
"All content is available under the Open Government Licence v3.0, except where otherwise stated".
I could not find the same export listed on data.gov.uk, so I name the GOV.UK service as the
portal.

The export labels each report Regime-1, Regime-2 or Regime-3, and I found no definition of the
labels on the publisher's pages. From the dates and the legislation, I infer that Regime-1 reports
were filed under the original 2017 rules. The other two were filed under amendments that apply from
2025 (statutory instruments SI 2024/444 and SI 2025/75). One amendment, SI 2024/444 (regulation
2(4)(d)), changed when a payment counts as made where a finance provider is involved. So the
analysis table (one row per company that reported in both periods), the three visual models, the
fitted model and the hypothesis test use Regime-1 reports only, and every figure they compare is
measured under one definition. Initial data analysis warns that variables that are not harmonised
can bring "inconsistent definitions" and "information bias" (Lusa et al., 2024, p. 26). The
screening for breaches of the code standard and late publication uses every report from all three
regimes, so its breach rates for periods ending in 2025 and 2026 come mostly from Regime-2 and
Regime-3 reports.

Contains public sector information licensed under the Open Government Licence v3.0.

## Data

- Export: <https://check-payment-practices.service.gov.uk/export/csv/>
- Downloaded: 6 Oct 2026
- File: `all_published_reports_20261006.csv`
- Size: 103,043,357 bytes (103 MB)
- SHA-256: `f9f2552222190b9c5f1ca145cdc1771ac88ba81c38fcfef49fe64c3b696db535`

The CSV is not in this repository because at 103 MB it is large raw data, which does not belong
in Git history, and some of its free-text columns hold contact email addresses. So it is supplied
in the submission zip instead.

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

   If you are working from the submission zip instead, unzip it and move into its one folder.
   That folder is the repository, with the dataset CSV already beside the notebook, so skip
   step 4.

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

Where the brief disagrees with itself or with its rubric, I follow the rubric unless that would
break the brief's own limits, and where the rubric cannot settle it, I meet both readings. Four points are worth stating here.

- The brief gives the report two file names, `module_summary.pdf` and
  `Statistical_Analysis_Report.pdf`, so I ship the same PDF under both.
- Four rubric rows are written for deep learning: they ask for training and evaluation results,
  notebook headings for model definition, training and evaluation, citations for deep learning
  concepts and training practices, and a complete deep learning experiment. The brief itself says "You are not training machine learning models yet", defines a
  visual model in this project as a chart, and limits the tools to Python, NumPy, pandas, Matplotlib,
  Seaborn, SciPy and Jupyter, with no deep learning library among them. So I train no deep
  learning model. To meet those rows as far as the brief allows, I use the rubric's own headings
  (data handling, model definition, training, evaluation, summary), and I add one fitted
  statistical model, a straight line from SciPy. I train it on reports ending in 2018 to 2022 and
  evaluate it on reports ending in 2023 to 2024, which it never sees.
- The brief asks for "at least one" hypothesis test in two places and "One" in two others, and the
  rubric says "One valid hypothesis test". So I designate exactly one, the paired t-test. The
  screening reports counts and rates only, and the other comparisons give means, medians or
  confidence intervals, not further tests.
- The brief and the rubric's Visualizations row ask for "at least three" visual models, but the
  rubric's Experimental Design row compares "the three different visual models", and its deep learning
  rows need a fitted model. So exactly three charts are
  labelled Visual model 1 to 3, and the fitted model's chart is labelled separately.

## References

Lusa, L., Proust-Lima, C., Schmidt, C. O., Lee, K. J., le Cessie, S., Baillie, M., Lawrence, F.,
Huebner, M., & TG3 of the STRATOS Initiative. (2024). Initial data analysis for longitudinal
studies to build a solid foundation for reproducible analysis. *PLOS ONE, 19*(5), Article
e0295726. https://doi.org/10.1371/journal.pone.0295726
