# Jenkins Python App

A Python app with a CI/CD pipeline built using Jenkins. The pipeline runs tests in parallel, packages the app, and deploys it, with a manual approval step before deployment.

## Tech stack
- Python, pytest, Jenkins

## How to run

```bash
git clone https://github.com/onujoy14/jenkins-python-app.git
cd jenkins-python-app
pip3 install pytest
python3 -m pytest test_app.py -v
```

## Pipeline stages

- Install dependencies
- Run tests in parallel
- Package the app into a zip
- Manual approval gate
- Deploy

## Author
Onu Joy Ojima · [onujoy14@gmail.com](mailto:onujoy14@gmail.com)
