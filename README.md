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

![image](https://github.com/EthanHuang0404/stroke-prediction/assets/52795694/a95d3b43-372e-4f9c-b18a-89e9d2b3b97a)

![image](https://github.com/EthanHuang0404/stroke-prediction/assets/52795694/3ef30492-002e-46f1-9aee-765053f652fd)

### Data Preprocessing
In this study, we process the physician's notes, which are written in English, by first standardizing the various forms of a single word back to their base form, or lemma. This is followed by removing non-letter characters such as numbers or punctuation marks, replacing them with spaces. Moreover, text data often includes frequently occurring but potentially insignificant words known as stop words, like articles, prepositions, and conjunctions. These words, while helping in sentence construction, do not contribute significantly to the content's essence. We employ a list of 421 stop words from Fox's research to filter out these extraneous words.

For the triage nurse's notes written mainly in Chinese, the initial step is to convert any English text and punctuation interspersed with Chinese from full-width to half-width characters. This conversion is crucial to prevent delays or errors during text segmentation. The text is then segmented into sentences based on punctuation marks such as commas, periods, and semicolons. Following this, we perform Chinese word segmentation and part-of-speech tagging using the CkipTagger package provided by the CKIP Lab (https://pypi.org/project/ckiptagger/). After segmentation, we remove stop words and selectively retain words based on their parts of speech, such as nouns, verbs, and adjectives, to maintain the relevance and importance of the terms in the dataset.
