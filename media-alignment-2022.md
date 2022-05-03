# Analysis of CCP-Aligned and Opposed Phrases

## Introduction



## Data

We scraped data from non-paywalled media in the following countries for the 
period of September 2021 to December 2021:
- Egypt (Arabic)
- France (French)
- India (English)
- Italy (Italian)
- Jordan (Arabic)
- Lebanon (Arabic)
- Spain (Spanish)
- UK (English)

## Methodology

We used a half-data-driven method (leveraging [this algorithm](https://www.cambridge.org/core/services/aop-cambridge-core/content/view/81B3703230D21620B81EB6E2266C7A66/S1047198700002291a.pdf/fightin_words_lexical_feature_selection_and_evaluation_for_identifying_the_content_of_political_conflict.pdf))
to identify noun phrases that are statistically over- and under-represented in the
English language PRC state media pertaining to the following salient topics, 
as well as a catch-all topic for PRC-related issues including Belt and Road, 
vaccines, South China Sea, etc:
- Hong Kong
- Huawei/TikTok
- Taiwan
- Xinjiang

We then manually filtered the noun phrases leaving those which express alignment
or opposition to CCP interests and ideology. The list can be viewed [here](https://github.com/doublethinklab/media-alignment-2022/blob/main/data.csv),
and a readable guide can be found [here](https://github.com/doublethinklab/media-alignment-2022/blob/main/phrase_guide.md).

Topic classification was performed as follows. We enumerated a set of core entities
involved in each topic and translated them into Arabic, French, Italian, and Spanish.
A document was classified as pertaining to a topic if it had at least three instances
of any entity in that topic. The entity lists can be found [here](https://github.com/doublethinklab/media-alignment-2022/blob/main/data.csv).

We then used string matching to identify instances of the phrases in the document text.
This is feasible as the target phrases are multi-word, and are highly unlikely to be 
substrings in other words.

## Findings

### Raw Results

Interested readers can explore the raw data of the findings in the following 
locations.

The raw data outputs are available in the following locations:
- [Phrase lists](https://github.com/doublethinklab/media-alignment-2022/blob/main/data.csv)
- [Document and topic counts](https://github.com/doublethinklab/media-alignment-2022/blob/main/doc_counts.csv).
- [Topic determinations with urls](https://github.com/doublethinklab/media-alignment-2022/tree/main/topics_urls).
- [Phrase counts](https://github.com/doublethinklab/media-alignment-2022/blob/main/phrase_counts.csv).
- [Entity counts](https://github.com/doublethinklab/media-alignment-2022/blob/main/entity_counts.csv).

Visualizations of the data are available in the following locations:
- [Plots of counts of each phrase per topic per country](https://github.com/doublethinklab/media-alignment-2022/tree/main/country_topic_phrases)
- [Plots of counts of each phrase per media per country](https://github.com/doublethinklab/media-alignment-2022/tree/main/media_topic_phrases)
- [Comparisons of usage of each phrase per article per country](https://github.com/doublethinklab/media-alignment-2022/tree/main/country_phrase_comparison)
- [Comparisons of usage of each phrase per article per media per country](https://github.com/doublethinklab/media-alignment-2022/tree/main/media_phrase_comparison)

### Selected Findings


