# Analysis of CCP-Aligned and Opposed Phrases

## Introduction

We empirically investigate the patterns of usage of CCP-aligned and
opposed phrases across media spaces pertaining to a set of topics relating to
core CCP interests. We hope to gain insight into the way these topics are 
presented to audiences in different countries and in different languages, and
to draw inferences about PRC influence in these media spaces if the data allows.

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

The results are presented in one of two ways:
1. as raw counts;
2. as a rate of phrase usage per article.

We find (1) is the most intuitive.
For (2), we also provide a 90% confidence interval, calculated from a binomial
distribution using the number of instances of the phrase, and the number of 
documents (either per media per topic, or per country per topic).
This provides a way to capture uncertainty when conducting comparisons.

## Limitations

Direct and indirect quotes are ubiquitous in news text data.
The relative amounts of attention given to CCP-aligned and opposed phrases
do not necessarily reflect PRC influence on a given media outlet or national media space.
Instead, these patterns of attention likely reflect editorial decisions to present
a balanced picture, often quoting PRC officials.

These comparisons cannot be considered comprehensive for three reasons.
First, we have only enumerated a subset of the potential aligned and opposed noun
phrase choices for these topics.
Second, we do not capture paraphrases of the subset we have identified.
Third, we believe our phrase lists are currently over-optimized for English.

Our topic classification methodology will involve some noise.
Some articles marked as about a given topic may not be so.

Some data sources are missing some articles due to scraping issues.
They cannot be considered complete article sets.

## Findings

### Raw Results

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

#### UK media coverage of Taiwan

We find that the most common CCP-aligned phrase about Taiwan in the UK media
is "reunification/reunify."

![UK Taiwan](/country_topic_phrases/UK-Taiwan.jpg?raw=true "UK Taiwan")

As our [guide](https://github.com/doublethinklab/media-alignment-2022/blob/main/phrase_guide.md) states,
this framing incorrectly assumes that the unification of Taiwan and the PRC was true at some
point in the past and is therefore aligned to CCP messaging.

This finding suggests that editors in the UK media should consider not using this
term when paraphrasing. If using direct quotes, the questionable assumption the 
term presupposes should be made clear to the reader.

We similarly find that the most CCP-opposed phrase is "Taiwanese". As our 
[guide](https://github.com/doublethinklab/media-alignment-2022/blob/main/phrase_guide.md) shows,
this is a term the CCP is keen to stamp out, particularly when referring to the
Taiwanese people, language, or government. The term does however appear in the
PRC state media, usually referring to companies or other organizations.

#### "Reunification"

We find that both Italy and the UK most prefer the term "reunification/reunify,"
followed by Spain.

![reunification](/country_phrase_comparison/reunification.jpg?raw=true "reunification")

![reunify](/country_phrase_comparison/reunify.jpg?raw=true "reunify")

We also break this down by media for Italy:

![Italy reunification](/media_phrase_comparison/Italy/reunification.jpg?raw=true "Italy reunification")

![Italy reuinfy](/media_phrase_comparison/Italy/reunify.jpg?raw=true "Italy reunify")

and UK:

![UK reunification](/media_phrase_comparison/UK/reunification.jpg?raw=true "UK reunification")

![UK reuinfy](/media_phrase_comparison/UK/reunify.jpg?raw=true "UK reunify")

We can see for Italy this pattern is lead by Ansa and tg24.
Ansa is noteworthy as they have republication agreements with the PRC state media.
We note, for example, the use of reunification in [this article](https://www.ansa.it/sito/notizie/mondo/asia/2021/12/29/cina-misure-drastiche-se-taiwan-verso-indipendenza_e627e93c-808f-42cd-957f-0b2904e4f62a.html) in our sample,
which reads like an unattributed PRC state media press release,
but is marked as an Ansa editorial.
This is certainly PRC influence, producing an article such as this.

For the UK, it is The Guardian and the Daily Mail leading usage of this term.
It is unlikely these editorial decisions are a function of PRC influence in 
these cases, as these newspapers have no know ideological or financial ties
to the CCP. We therefore suggest that editors of these newspapers think 
carefully about usage of this term.

#### "Taiwanese"

Usage of the term "Taiwanese" is generally high, especially for the UK.
It appears to be salient that the lowest rates of usage of this term come
from Spain and Italy.

![Taiwanese](/country_phrase_comparison/Taiwanese.jpg?raw=true "Taiwanese")

This is consistent with the view that the UK media's relatively high usage of 
"reunification/reunify" represents questionable editorial decisions and not PRC
influence. On the other hand, it supports the view that the Italian and Spanish
media report on Taiwan in a way more consistently aligned with CCP ideology.
