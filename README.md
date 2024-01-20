## Introduction
Dizziness or vertigo is a common complaint in emergency departments. After ruling out general conditions like anemia, emergency physicians must distinguish between benign peripheral vestibular disorders and serious central nervous system issues, notably strokes. In the U.S., around 4.4 million emergency visits yearly are for dizziness or vertigo, with 34% due to benign vestibular disorders and 3-5% from strokes, particularly in the brainstem or cerebellum.

Differentiating strokes in such cases is challenging. Strokes causing dizziness often have small lesions in the brainstem or cerebellum, leaving major pathways unaffected. This means routine neurological tests may seem normal, and typical stroke symptoms like facial droop or limb weakness might not be present. Studies show that strokes with initial vestibular symptoms are missed in 35% of emergency cases, compared to 4% for strokes with unilateral motor weakness. Even skilled neurologists can miss these subtle signs, like Horner’s syndrome or hoarseness, as they require specific examination techniques not commonly used in emergency settings.


## Dataset
The dataset used in this research originates from a hospital in Taiwan. In constructing the predictive model, patient characteristics serving as independent variables are categorized into structured and unstructured data. Structured data encompasses critical elements such as stroke risk factors, including hypertension and diabetes, along with vital signs like blood pressure and heart rate. Unstructured data includes emergency physicians' medical records and triage notes prepared by nurses. The study's dependent variable is the diagnosis of a stroke, be it ischemic or hemorrhagic, within a 14-day period following an emergency department visit. The confirmation of stroke diagnoses is conducted either through the hospital’s stroke registry or by employing ICD codes from medical records, in accordance with established validation rules.

The table below presents the distribution of data across two categories: the stroke class (labeled as '0') and the non-stroke class (labeled as '1').

| Label | Training Set | Test Set |
| :---         |     :---:      |          ---: |
| 0 | 17,465   | 5,092   |
| 1   | 531   | 135      |

## Method
The images included offer an overview of the methodologies applied in this study, which incorporates two distinct approaches: a machine learning approach and a deep learning approach.

<img src="https://github.com/EthanHuang0404/stroke-prediction/assets/52795694/a95d3b43-372e-4f9c-b18a-89e9d2b3b97a" width="600" height="600"><br>
Figure 1: Machine Learning Approach


<img src="https://github.com/EthanHuang0404/stroke-prediction/assets/52795694/3ef30492-002e-46f1-9aee-765053f652fd" width="600" height="600"><br>
Figure 2: Deep Learning Approach



### Data Preprocessing
**Processing of Physician's Notes (English):**
* Standardization: Convert various forms of words back to their base form or lemma.
* Removal of Non-letter Characters: Eliminate numbers and punctuation, replacing them with spaces.
* Stop Words Removal: Use a list of 421 stop words from Fox's research to filter out common but insignificant words like articles, prepositions, and conjunctions.

**Processing of Triage Nurse's Notes (Chinese):**
* Conversion of Characters: Change interspersed English text and punctuation from full-width to half-width characters for accurate text segmentation.
* Sentence Segmentation: Segment text based on standard punctuation marks such as commas, periods, and semicolons.
* Word Segmentation and POS Tagging: Utilize the CkipTagger tool from CKIP Lab for Chinese word segmentation and part-of-speech tagging.
* Stop Words Removal and Retention of Significant Words: Similar to English notes, remove stop words and retain important words based on their parts of speech for contextually relevant data.
