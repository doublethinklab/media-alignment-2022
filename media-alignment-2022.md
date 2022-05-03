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

Our topic classification methodology will involve some noise.
Some articles marked as about a given topic may not be so.

Some data sources are missing some articles due to scraping issues.
They cannot be considered complete article sets.

In many cases, the number of observations (i.e. articles about a topic) are 
in the hundreds, making the findings relatively robust (also shown by the 90%
confidence intervals). However, we believe our study needs to run over a longer
timeframe to improve the robustness of the findings.

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

The following shows the relative attention given to each topic averaged over
all media in all countries:

![Topics per Country](/topic_coverage/per_country.jpg?raw=true "Topics per Country")

#### UK

The relative attention give to each topic per media is:

![Topics per Media UK](/topic_coverage/UK-per_media.jpg?raw=true "Topics per Media UK")

Other than our catch-all, general, `China` topic, in our sampling period the UK
media appear most interested in the Xinjiang topic. Sky appears to have relatively
little interest in Taiwan, although relatively interested in Hong Kong.

We therefore start by looking at the Xinjiang topic.

![UK Xinjiang](/country_topic_phrases/UK-Xinjiang.jpg?raw=true "UK Xinjiang")

As expected, the UK media overall are not shy about reporting on human rights
abuses in Xinjiang. One finding, which we will return to for UK, is that there
is a relatively high usage rate of the phrase `anti-China` in virtually every
topic. The phrases `alleged human rights abuses` and `religious extremism` are
also highly featured aligned phrases in the UK, both appearing nearing 40 times.

As expected, a random sample of these documents indicates that most  
(likely) [indirect quotes](https://news.sky.com/story/winter-olympics-2022-china-warns-uk-us-and-australia-will-pay-the-price-for-diplomatic-boycott-of-beijing-games-12490517),
but [not all](https://www.bbc.com/news/business-57830856).
The choice of this phrase could be considered an attempt to appear editorially neutral, 
however, at this point in time, we argue that the weight of evidence of crimes
against humanity in Xinjiang makes this word choice less rather than more neutral.
The BBC appears to stand out as the most likely to make this editorial decision.

![UK alleged human rights abuses](/media_phrase_comparison/UK/alleged human rights abuses.jpg?raw=true "UK alleged human rights abuses")

A random sample of the appearances of `religious extremism` appear to be attempts
at editorial balance, [indirectly](https://www.dailymail.co.uk/wires/reuters/article-10476893/Olympics-Putin-Xi-mix-politics-sport-unveiling-alliance-Olympics.html) quoting PRC officials.
Daily Mail and The Independent are most likely to make this editorial choice.

![UK religious extremism](/media_phrase_comparison/UK/religious extremism.jpg?raw=true "UK religious extremism")

The Independent is an interesting case in light of the publication’s ownership 
and a November 18, 2021 deal to begin publishing the China Daily-issued 
“China Watch” articles.
Although this is a clear vector of PRC influence, our data does not yet paint a 
clear picture of patterns of over-alignment and under-opposition at The Independent.
They are not shy about using opposed phrases, and, overall, their patterns
os using our aligned phrases are not noticeably out-of-step with the rest of the 
UK media studied.

The Daily Mail's preference for the term `religious extremism` may or may not
extend from their well-known preference for xenophobia. We argue that 
distracting from the horrific human rights abuses 
occuring in Xinjiang by giving undue attention to the CCP's 
preferred framing of their actions as countering "terrorism" and "religious extremism" is a 
terrible editorial decision.

The topic with the second highest attention in UK is Hong Kong.

![UK Hong Kong](/country_topic_phrases/UK-Hong Kong.jpg?raw=true "UK Hong Kong")

As expected, the UK media shows significant editorial balance in reporting on
Hong Kong issues, and does not shy away from CCP-opposed framings of protests
as relating to democracy issues. On the opposed side, we once again see `anti-China`
sticking out. 

This is also very apparent in our catch-all "China" topic.

![UK China](/country_topic_phrases/UK-China.jpg?raw=true "UK China")

The Independent leads in preference for attention given to the phrase
`new Cold War`.

![UK new Cold War](/media_phrase_comparison/UK/new Cold War.jpg?raw=true "UK new Cold War")

Notably, this term appears in [opinion](https://www.independent.co.uk/voices/culture-wars-boris-johnson-threat-to-uk-b1885436.html), 
not as quotes, in the Independent.
This may or may not be ideological alignment between the CCP and The Independent.

The BBC has the lead on using the phrase `Cold War mentality`.

![UK Cold War mentality](/media_phrase_comparison/UK/Cold War mentality.jpg?raw=true "UK Cold War mentality")

However, this is largely accounted for by [quoting PRC officials](https://www.bbc.com/news/world-europe-58610234).

This brings us to `anti-China`. By quite a margin, the Daily Mail leads in
the use of this phrase.

![UK anti-China](/media_phrase_comparison/UK/anti-China.jpg?raw=true "UK anti-China")

This likely somewhat accounts for the large lead the UK has over the other
countries studied in the average use of this phrase, but not entirely.

![anti-China](/country_phrase_comparison/anti-China.jpg?raw=true "anti-China")

We see that the Guardian is above the mean of the second place country, India, 
and that The Independent and BBC are both well above all other countries in our
sample.

We believe this is a significant finding and one that requires serious thought.
The label `anti-China` is not often self-given and is a thought-terminating cliche
often thrown as a smear.
A recent topical example in the English language media sphere comes from 
Australia, where the [Australian Financial Review](https://twitter.com/drewpavlou/status/1520952101408440320?s=21&t=HXPSs33VyjNAVlb2aRQ96A) (considered to be more
PRC-aligned in Australia due to elite capture of Australia's business elites)
labeled self-identifying pro-China, anti-CCP activist Drew Pavlou as "anti-China."
This label plays into the hands of CCP propaganda by equating the CCP with "China,"
and therefore criticism of the CCP as criticism of China, and even, to some minds,
as *racist*.
Needless to say, this is a label that is also opposed by [Chinese Australians](https://twitter.com/badiucao/status/1520999889492406273?s=21&t=HXPSs33VyjNAVlb2aRQ96A).



#### Taiwan

##### UK media coverage of Taiwan

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

##### "Reunification"

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

We can see for Italy this pattern is lead by ANSA and tg24.
ANSA is noteworthy as they have republication agreements with the PRC state media.
We note, for example, the use of reunification in [this article](https://www.ansa.it/sito/notizie/mondo/asia/2021/12/29/cina-misure-drastiche-se-taiwan-verso-indipendenza_e627e93c-808f-42cd-957f-0b2904e4f62a.html) in our sample,
which reads like an unattributed PRC state media press release,
but is marked as an ANSA editorial.
This is certainly PRC influence, producing an article such as this.

For the UK, it is The Guardian and the Daily Mail leading usage of this term.
It is unlikely these editorial decisions are a function of PRC influence in 
these cases, as these newspapers have no known ideological or financial ties
to the CCP. We therefore suggest that editors of these newspapers think 
carefully about usage of this term in the future.

##### "Taiwanese"

Usage of the term "Taiwanese" is generally high, especially for the UK.
It appears to be salient that among the lowest rates of usage of this term 
include Spain and Italy.

![Taiwanese](/country_phrase_comparison/Taiwanese.jpg?raw=true "Taiwanese")

This is consistent with the view that the UK media's relatively high usage of 
"reunification/reunify" represents questionable editorial decisions and not PRC
influence. On the other hand, it supports the view that the Italian and Spanish
media report on Taiwan in a way more consistently aligned with CCP ideology.
It is consistent that ANSA and tg24 show the lowest usage of the term in Italy.

![Italy Taiwanese](/media_phrase_comparison/Italy/Taiwanese.jpg?raw=true "Italy Taiwanese")

It appears that the French media are generally less interested in the Taiwan
topic, however it is also possible that the limitations of our methodology
have missed salient French language phrases that may tell a different picture.

![France Taiwan](/country_topic_phrases/France-Taiwan.jpg?raw=true "France Taiwan")

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
