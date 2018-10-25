[![spaCy](https://img.shields.io/badge/built%20with-spaCy-09a3d5.svg)](https://spacy.io)
# medaCy
:hospital: Medical Natural Language Processing with spaCy :hospital:

MedaCy is a text processing and learning framework built over spaCy to support the lightning fast prototyping, building, and application of highly predictive named entity recognition and relationship extraction systems in the medical domain.

![alt text](https://nlp.cs.vcu.edu/images/Edit_NanomedicineDatabase.png "Nanoinformatics")

Features
========
- Highly predictive out-of-the-box trained models for clinical named entity recognition and relationship extraction.
- Customizable feature extraction pipelines for custom model building.
- Integrated converters for common text annotation formats (Prodigy, BRAT, etc).
- Pre-compiled medical terminology and abbreviation lexicons.


User Guide
==========
Using medaCy is simple: all one needs is to select a pipeline and provide it with training data to learn from.

A learning script utilizing Metamap
```python
from medacy.pipelines import ClinicalPipeline
from medacy.tools import DataLoader
from medacy.pipeline_component import MetaMap

from medacy.learn import Learner

#Some more powerful pipelines require an outside knowledge source such as MetaMap.
metamap = MetaMap(metamap_path="/home/share/programs/metamap/2016/public_mm/bin/metamap")

#Automatically organizes your training files.
train_loader = DataLoader("/directory/containing/your/training/data/")

#Pre-metamap our training data to speed up building models.
train_loader.metamap(metamap)

#Create pipeline and specify entities to learn.
pipeline = ClinicalPipeline(metamap, entities=['Strength'])

#create a Learner using our pipeline and data
learner = Learner(pipeline, loader)

#Build a model (defaults to Conditional Random Field)
model = learner.train()

```

License
=======
This package is licensed under the GNU General Public License


Authors
=======
Andriy Mulyar, Bobby Best, Steele Farnsworth, Yadunandan Pillai, Corey Sutphin, Bridget McInnes

Acknowledgments
===============
- [VCU Natural Language Processing Lab](https://nlp.cs.vcu.edu/)     ![alt text](https://nlp.cs.vcu.edu/images/vcu_head_logo "VCU")
- [Nanoinformatics Vertically Integrated Projects](https://rampages.us/nanoinformatics/)