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
Instead, these patterns of attention may reflect editorial decisions to present
a balanced picture, quoting PRC officials.

These comparisons cannot be considered comprehensive for three reasons.
First, we have only enumerated a subset of the potential aligned and opposed noun
phrase choices for these topics.
Second, we do not capture paraphrases of the subset we have identified.
Third, we believe our phrase lists are currently over-optimized for English.
By that we mean that our phrase lists were developed from English data, and are
therefore better suited to capture the way alignment and opposition is expressed in English.
For example, the term “النظام الصيني”  translates into Arabic as “the Chinese regime,” a term that carries negative connotations towards that entity and is often used in Arab media to describe opposing governments, for instance the “Syrian Regime.” 
However, when reviewing one of the articles that used that term, we found the context in which that phrase was used is very different. 
The term was referring (in a positive manner) to the new Chinese weapons system (shorthand, the “Chinese System” which is written the same way as the “Chinese Regime” in Arabic but carries a very different meaning). 
Another article that used that same phrase was a positive article noting that the Chinese (super computer) system was the fastest in the world.
This is an example where the (correct) translation can return inconsistent results.
We suspect we are also just missing too many important phrases in languages other than English.

Our topic classification methodology will involve some noise.
Some articles marked as about a given topic may not be so.

Some data sources are missing some articles due to scraping issues.
They cannot be considered complete article sets.

In many cases, the number of observations (i.e. articles about a topic) are 
in the hundreds, making the findings relatively robust (also shown by the 90%
confidence intervals). However, we believe our study needs to run over a longer
timeframe to improve the robustness of the findings.

Finally, the breadth of our topics is limited and likely also over-optimized for salience in the English language media we studied.

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
- [Comparisons of number of articles addressing each topic](https://github.com/doublethinklab/media-alignment-2022/tree/main/topic_coverage)

### Selected Findings

Please follow these links to selected findings for each country:
- [UK](https://github.com/doublethinklab/media-alignment-2022/blob/main/UK-analysis.md)
- [India](https://github.com/doublethinklab/media-alignment-2022/blob/main/India-analysis.md)
- [Italy](https://github.com/doublethinklab/media-alignment-2022/blob/main/Italy-analysis.md)
- [Egypt](https://github.com/doublethinklab/media-alignment-2022/blob/main/Egypt-analysis.md)
- [Jordan](https://github.com/doublethinklab/media-alignment-2022/blob/main/Jordan-analysis.md)
- [Lebanon](https://github.com/doublethinklab/media-alignment-2022/blob/main/Lebanon-analysis.md)
- [France](https://github.com/doublethinklab/media-alignment-2022/blob/main/France-analysis.md)
- [Spain](https://github.com/doublethinklab/media-alignment-2022/blob/main/Spain-analysis.md)

## Future Work

To improve on the items listed in the **Limitations** section.

We want to run this over a longer period of time, addressing the data collection
process in order to obtain complete article sets.

We believe our methodology is over-optimized for English. In general we see
a greater number and variety of phrase hits in English language than other 
languages, suggesting that our approach of identifying phrases over- and under-represented
in English state media, and then translating to other languages, results in 
phrase sets better suited for English and less able to capture salient aspects
of word choice in other languages. A better approach would be to identify 
phrases separately in each linguistic context, and then to bring them all together.

We want to expand the size and coverage of our phrase lists to push them as close
to comprehensive as possible. Doing so should allow us to make more general 
observations and comparisons about the levels of alignment and opposition overall
in these media spaces, and for particular media. This will require half-data-driven 
qualitative analysis in each language as a first step.

Another part of that will be to address the computational challenges in detecting
noun phrase paraphrases automatically. We found multilingual paraphrase models
to be more accurate in some languages than others given our current phrase set.
This may require hand-labeling some data and fine-tuning existing paraphrase 
models. This would also allow us to address verb phrases (such as `smear china`),
which are more syntactically complex and require paraphrase detection even more.
This was our reason for restricting the present work to noun phrases.

Finally, our topic classification method could be improved. At the least, we 
need to estimate the level of noise in the current approach.

We would also like to expand our phrase lists enough to address topics such as
Belt and Road independently, and expand our topic list overall. We will need to
monitor the changing conversation in news media over time to watch for new
developments and salient phrases that emerge as world events unfold.

## Acknowledgements

We warmly thank our in-country experts for contributing to the analyses and translations.
- Jad Melki: Egpyt, Jordan, Lebanon
- David Green: UK
- Maya Mirchandani: India
