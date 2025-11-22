# Kommunalvalg25 Candidate test analysis
Finding your top election candidate based on Principal Component Analysis

### Context

Last week I got an invitation to vote in Kommunalvalg in Copenhagen. I was excited to get it, but knew little about the political landscape of the municipality (maybe 2 biggest parties).

For people like me Danish news outlets like [DR](https://www.dr.dk/nyheder/politik/kommunalvalg/kandidattest) and [TV2](https://nyheder.tv2.dk/kandidattest) created tests designed to help you find the candidates whose views on the hottest issues align the most with yours. I took them both and got some recommendations, but didn't feel very aligned with my top suggestions.

So, I decided to use the published answers to make my own test and see if I get different results.

  
### Who is this for

  
- First-time voters who want to understand the landscape in general.
- Foreigners interested in local politics of Copenhagen.
- Copenhageners who want to challenge their bias.
  
Although I'm sure that to Danes most of my findings will be obvious, and they can contextualize them much better.

### DR and TV2 Kandidattest comparison

The tests contain 19-25 questions on the most popular issues. Some questions can be skipped, and some can be marked as "especially important". Once completed, the test will match you with the candidates that have the closest answers to yours based on Euclidean distance with weights.
  

1. **Question presentation**

- DR: One question per page. It is possible to view "For" and "Against" arguments.
- TV2: One question per page. No arguments provided.

I think in general, showing arguments creates bias, but they are not automatically visible, so people only view them when in doubt.


2. **Answer scale**

- DR: 4-point scale. Uenig - Lidt Uenig - Lidt Enig - Enig
- TV2: 5-point scale: Helt uenig - Uenig - Neutral - Enig - Helt enig

I personally prefer DR's scale because it presents 2 middle options as variations of neutral, but allows to see your inclination while omitting 'true neutral'.


3. **Question phrasing**
  
- DR's questions are more open-ended.
	- Københavns Kommune skal fremme opførelsen af flere almene lejeboliger.
- TV2 frames them as a spectrum between 2 priorities.
	- Kommunen bør arbejde for, at der kan opføres flere billige lejeboliger, og at dette prioriteres på bekostning af ejerboliger samt kommunens profit på salg af byggegrunde.
  
On one hand, TV2 questions use the language from candidates' key issues (mærksager), so this phrasing might help to get a better feeling of specific candidate's position. On another hand, this approach may force candidates who propose alternative solutions into neutral answers and bundle them together with those who don't prioritise the topic in question (i.e. housing).

4. **'Especially important' issues**

- DR gives you an option to label the questions when you first see them.
- TV2 lets you choose 2 top areas (not questions) after answering all the questions.

5. **Result presentation**

- DR shows you top candidate matches. When opening the candidate page you can see their whole survey with your and their answers marked.
- TV2 shows both **candidates and parties** and summarizes your top agreement and disagreement areas with the top candidate.

I think including party alignment is great because it's important to know what the party stands for if your top candidate doesn't get a seat.
  

#### Key takeaways

Overall, I found **TV2**'s test more **user-friendly and informative**, but **DR**'s test to have a **better scale** and slightly better question phrasing, so I'll take the DR data for the analysis.

#### DR kandidattest: dataset description

Each candidate  filled **3 Mærksager** (Key Issues) and completed a survey with **19 questions** , 4 questions could be skipped. I assigned the following numeric values to the answers.

- Uenig 🙁 : -2
- Lidt Uenig 😕: -1
- Lidt Enig 🙂: 1
- Enig 😃: 2

 For the sake of this analysis I excluded the candidate names and kept only their parties and anonymous ids.

### Data overview
- Parties and candidates: 24 Parties and 261 candidate, maximum 30 candidates per party.
- Missing key issues: 218 candidates submitted both the test and Key Issues, 11 submitted only the test.

<bar_chart>

### Directional agreement
How much does response direction (positive or negative) vary within each party?
The smaller the party, the lower the standard variation, so I will only look at the parties with at least 10 candidates who completed the survey.

**Key insights:**

- Most big parties (<b><font  color="#7DAE00">C</font>, <font  color="#D00000">A</font>, <font  color="#1041C0">V</font>, <font  color="#E600A8">F</font></b>). have **3-6** items on their agenda that they agree on, and have a mix of opinions about other topics.
- Enhedslisten <font  color="#F25700"><b>(Ø)</b></font> lives up to its name: despite being a larger party it has the <b><font  color="#F25700">lowest variance of responses</font></b>, and its members directionally agree on **13 of 19** questions.
- Liberal Alliance <font  color="#00A8D9"><b>(I)</b></font> and Alternativet <font  color="#237B2D"><b>(Å)</b></font>directionally agree on **10** questions within the parties.

<heatmap1>

### Response variance

Which questions have the lowest variance? 

**Answer scale**:<br>
Uenig 😡 - Lidt Uenig ☹️ - Lidt Enig 🙂 - Enig 🥰
<br><br>
**Color scale interpretation**:
- <font color="#3a4487"><b>Dark blue</b></font>: identical answers, usually extreme
- <font color="#4C72B0"><b>Blue</b></font>: same direction, different magnitude (🙂 vs 🥰) or (☹️ vs 😡)
- White: answers range between 2 neutrals (🙂 vs ☹️)
- <font color="#F4B150"><b> Orange</b></font>: answers range between an extreme and a neutral in different direction (🙂 vs 😡) or (🥰 vs ☹️)
- <font color="#e48b0e"><b> Bright orange</b></font>: answers range between 2 extremes (🥰 vs 😡)
Usually 0 variance would come from extreme responses (2 or -2) and show what are the issues that define the parties.
<br>

**Key insights**:

- The most burning question across all parties:
  - **KK skal fremme opførelsen af flere almene lejeboliger** got unanimous and extreme (positive or negative) responses in several parties (<b><font color="#E600A8">F</font>, <font color="#F25700">Ø</font>, <font color="#5ABE82">Q</font>, <font color="#D00000">A</font>, <font color="#00A8D9">I</font></b>).

- Strong agreement within the parties
   - Liberal Alliance <font color="#00A8D9"><b>(I)</b></font>: mosques, Lynetteholmen, green energy, culture
   - Enheslisten <font color="#F25700"><b>(Ø)</b></font>: mosques, Lynetteholmen, green energy, culture
   - Frie Grønne <font color="#5ABE82"><b>(Q)</b></font>: mosques, green energy, free meals in schools


- Strong opposing opinions within Frie Grønne <font color="#5ABE82"><b>(Q)</b></font>
   - The answers suggest disagreement on taxes, schools and high-rise buildings (q4, q10, q16).
 
### PCA: Top questions influencing the axes.

#### PC1
Candidates who score high on this axis are likely to:
- Agree with q13, q10, q4, q1, q18, and disagree with q19 and q5.
- General theme:
- **More parking spaces, privatize welfare, keep taxes and services low**. <br>

The candidates who scored low on this scale have opposing views: want to invest into welfare and public transport.
This axis represents a traditional <b><font color="#1041C0">"business</font> vs <font color="#D00000">welfare"</font></b> orientation. <br>

#### PC2
Candidates who score high on this axis are likely to:
- Agree with q11, q13, q16, q17, q8, and disagree with: q19.
- General theme:
- **Changes in schools** (ensure diversity, isolate disruptive students, provie free lunch), **more parking spaces, reduce high-rise construction, tax increase.**

The candidates who scored low on this scale have opposing views: don't believe in akutscoler, rely on public transport, support high-rise buildings, oppose tax increase.
This axis measures orientation on <b><font color="#F2A900">"families</font> vs <font color="#7DAE00"> youth"</font></b> .

**Note**: The questions related to **parking** contribute to **both axes**.
This means that combined with other questions, scoring high on this topic can mean that you are leaning <b><font color="#1041C0">business</font></b> and/or <b><font color="#F2A900">family</font></b>.
