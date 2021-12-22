<p align='center'>
  <img src='https://github.com/ArtLabss/open-data-anonimizer/blob/faca437a7675572306aba35824287f174edd230f/examples/artLabs_new.png' >
</p>
<h1 align='center'>anonympy 🕶️</h1>

<p align='center'>
<img src="https://img.shields.io/github/forks/ArtLabss/open-data-anonimizer.svg">
  <img src="https://img.shields.io/github/stars/ArtLabss/open-data-anonimizer.svg">
  <img src="https://img.shields.io/github/watchers/ArtLabss/open-data-anonimizer.svg">
  <img src="https://img.shields.io/github/last-commit/ArtLabss/open-data-anonimizer.svg">
  <br>
  <img src="https://img.shields.io/pypi/v/anonympy.svg">
  <img src="https://img.shields.io/pypi/l/anonympy.svg">
  <img src="http://hits.dwyl.com/ArtLabss/open-data-anonimizer.svg?style=flat">
  <br>
  With :heartpulse: by ArtLabs
  
<h2>Overview</h2>
<p>A general Python library for data anonymization of tabular, text, image and sound data. See <a href="https://artlabs.tech/projects/">ArtLabs/projects</a> for more or similar projects.</p>
<br>
<h2>Main Features</h2>

<p><strong>Tabular</strong></p>

<ul>
  <li>Ease of use</li>
  <li>Efficient anonymization (based on pandas DataFrame)</li>
  <li>Numerous anonymization techniques (perturbation, tokenization, synthetic data ...)</li>
</ul>

<p><strong>Text, Image, Sound</strong></p>
<ul>
  <li>In development</li>
</ul>

<br>

<h2>Installation</h2>

<h3>Dependencies</h3>
<ol>
  <li> Python (>= 3.7)</li>
  <li>cape-privacy</li>
  <li>faker</li>
  <li>scikit-learn</li>
  <li>pandas</li>
  <li>numpy</li>
  <li><a href="https://github.com/ArtLabss/open-data-anonimizer/blob/main/requirements.txt">    . . .</a></li>
</ol>

<h3>Install with pip</h3>

<p>Easiest way to install anonympy is using <code>pip</code></p>

```
pip install cape-privacy==0.3.0 --no-deps 
```
<p>Due to conflicting pandas/numpy versions with <a href="https://github.com/capeprivacy/cape-python/issues/112">cape-privacy</a>, it's recommend to install them seperately</p>

```
pip install anonympy
```

<h3>Install from source</h3>

<p>Installing the library from source code is also possible</p>

```
git clone https://github.com/ArtLabss/open-data-anonimizer.git
cd open-data-anonimizer
pip install -r requirements.txt
make bootstrap
pip install cape-privacy==0.3.0 --no-deps 
```

<br>

<h2>Usage Example </h2>

<p>You can find more examples <a href="https://github.com/ArtLabss/open-data-anonimizer/blob/main/examples/pandas.ipynb">here</a>

```python
from anonympy.pandas import dfAnonymizer
from anonympy.pandas.utils import load_dataset

df = load_dataset() 
print(df)
```

|   |  name | age |  birthdate |   salary |                                  web |                email |       ssn |
|--:|------:|----:|-----------:|---------:|-------------------------------------:|---------------------:|----------:|
| 0 | Bruce | 33  | 1915-04-17 | 59234.32 | http://www.alandrosenburgcpapc.co.uk | josefrazier@owen.com | 343554334 |
| 1 | Tony  | 48  | 1970-05-29 | 49324.53 | http://www.capgeminiamerica.co.uk    | eryan@lewis.com      | 656564664 |
  
```python
# Calling the generic Function
anonym = dfAnonymizer(df)
anonym.anonymize(inplace = False) # changes will be returned, not applied
```

|      | name            | age    | birthdate  | age     | web        |         email       |     ssn     |
|------|-----------------|--------|------------|---------|------------|---------------------|-------------|
| 0    | Stephanie Patel | 30     | 1915-04-17 | 60000.0 | 5968b7880f | pjordan@example.com | 391-77-9210 |
| 1    | Daniel Matthews | 50     | 1971-01-21 | 50000.0 | 2ae31d40d4 | tparks@example.org  | 872-80-9114 |
  
```python
# Or applying a specific anonymization technique to a column
from anonympy.pandas.utils import available_methods

anonym.categorical_columns
... ['name', 'web', 'email', 'ssn']
available_methods('categorical') 
... categorical_fake	categorical_fake_auto	categorical_resampling	categorical_tokenization	categorical_email_masking
  
anonym.anonymize({'name': 'categorical_fake', 
                  'web': 'categorical_tokenization', 
                  'email':'categorical_email_masking', 
                  'ssn': 'categorical_fake'})
print(anonym.to_df())
```
|   |  name | age |  birthdate |   salary |                                  web |                email |       ssn |
|--:|------:|----:|-----------:|---------:|-------------------------------------:|---------------------:|----------:|
| 0 | Paul Lang | 33  | 1915-04-17 | 59234.32 | 8ee92fb1bd | j*****r@owen.com | 792-82-0468 |
| 1 | Michael Gillespie  | 48  | 1970-05-29 | 49324.53 | 51b615c92e    | e*****n@lewis.com      | 762-13-6119 |
  
<br>

<h2>Development</h2>

<h3>Contributions</h3>

<p>The <a href="https://github.com/ArtLabss/open-data-anonimizer/blob/main/CONTRIBUTING.md">Contributing Guide</a> has detailed information about contributing code and documentation.</p>

<h3>Important Links</h3>
<ul>
  <li>Official source code repo: <a href="https://github.com/ArtLabss/open-data-anonimizer">https://github.com/ArtLabss/open-data-anonimizer</a></li>
  <li>Download releases: <a href="https://pypi.org/project/anonympy/">https://pypi.org/project/anonympy/</a></li>
  <li>Issue tracker: <a href="https://github.com/ArtLabss/open-data-anonimizer/issues">https://github.com/ArtLabss/open-data-anonimizer/issues</li></a>
</ul>

<h2>License</h2>

<p><a href="https://github.com/ArtLabss/open-data-anonimizer/blob/main/LICENSE">BSD 3</a></p>


<h2>Code of Conduct</h2>
<p>Please see <a href="https://github.com/ArtLabss/open-data-anonimizer/blob/main/CODE_OF_CONDUCT.md">Code of Conduct</a>. 
All community members are expected to follow it.</p>
