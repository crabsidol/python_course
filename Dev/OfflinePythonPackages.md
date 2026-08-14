# Offline Python Packages

Layout:

```text
project-root/
  .venv/
  requirements.txt
  wheelhouse/
  *.ipynb
```

## Generate `wheelhouse`

Online:

```bash
source .venv/bin/activate

pip install -U pip
pip install numpy pandas matplotlib scipy scikit-learn seaborn jupyter ipykernel openpyxl requests

pip freeze > requirements.txt

rm -rf wheelhouse
mkdir wheelhouse
pip download -r requirements.txt -d wheelhouse
```

## Install offline

```bash
source .venv/bin/activate
pip install --no-index --find-links=wheelhouse -r requirements.txt
```

## VS Code Jupyter kernel

```bash
python -m ipykernel install --user --name offline-data --display-name "Python offline-data"
```
