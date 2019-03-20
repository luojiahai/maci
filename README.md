# maci

In the context of Interpretable Machine Learning, we define Contrastive Interpretation as an instance and its counter-factual case. We use perturbative approach to generate counter-factual instances.

This program generates a counter-factual instance from a given instance and a binary classifier. The algorithm is: (1) sample around the instance, (2) predict all samples using the predict function of the classifier, (3) calculate distances between samples and the instance, (4) find the sample that is predicted as the opposite class and has the smallest distance.

## run

python 3.5.2

```pip3 install -r requirements```

```python3 main.py```

## tabular interpretation

```
plain instance: [50. 50.]
counter-factual instance: [73.84056924 51.69836722]
plain instance prediction: in
plain instance predict proba: [1.41799091e-06 9.99998582e-01]
counter-factual instance prediction: out
counter-factual instance predict proba: [0.56547189 0.43452811]
distance: 0.817063837363493
```

## tabular interpretation (loan dataset)

```
plain instance: [1. 4. 1. 0. 0. 0. 3. 3. 1.]
counter-factual instance: [1. 4. 1. 0. 0. 0. 0. 0. 1.]
plain instance prediction: Good Loan
plain instance predict proba: [0.82648734 0.17351266]
counter-factual instance prediction: Bad Loan
counter-factual instance predict proba: [0.16351895 0.83648105]
distance: 1.4142135623730951
counter-factual description:
-- from last_fico_range_high > 749.00 to last_fico_range_high <= 649.00
-- from last_fico_range_low > 745.00 to last_fico_range_low <= 645.00
```

```
plain instance: [3. 4. 1. 3. 1. 3. 0. 0. 1.]
counter-factual instance: [3. 4. 1. 3. 1. 3. 0. 2. 1.]
plain instance prediction: Bad Loan
plain instance predict proba: [0.16572486 0.83427514]
counter-factual instance prediction: Good Loan
counter-factual instance predict proba: [0.68064872 0.31935128]
distance: 1.0
counter-factual description:
-- from last_fico_range_low <= 645.00 to 695.00 < last_fico_range_low <= 745.00
```

## text interpretation

bug found, to be fixed...

## note
this software is implemented based on the implementation of LIME (https://github.com/marcotcr/lime)
