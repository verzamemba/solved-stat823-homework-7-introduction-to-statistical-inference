Download Link: https://assignmentchef.com/product/solved-stat823-homework-7-introduction-to-statistical-inference
<br>
Using RMarkdown in RStudio, complete the following questions. Launch RStudio and open a new RMarkdown file or use the class RMarkdown template provided and save it on your working directory as a .Rmd file. At the end of the activity, save your <strong>pdf </strong>generated from RMarkdown+Knitr and submit your homework on the Blackboard.

<h1>1               Analyzing Data with a Categorical Outcome</h1>

Binge drinking is defined by the National Institute on Alcohol Abuse and Alcoholism (NIAAA) as a pattern of drinking that brings blood alcohol concentration (BAC) levels to 0.08 g/dL. This typically occurs after 4 drinks for women and 5 drinks for men in about 2 hours. The Substance Abuse and Mental Health Services Administration (SAMHSA) conducts an annual National Survey on Drug Use and Health (NSDUH) and defines binge drinking as drinking 5 or more alcoholic drinks on the same occasion on at least 1 day in the past 30 days. In 2014, 24.7 percent of people ages 18 or older reported that they engaged in binge drinking in the past month. To assess the level of binge drinking on campus, University A conducted a survey of alcohol use of undergraduate students. A random sample of 1300 undergraduate students were classified as to whether they reported engaging in binge drinking in the last month:

Page -1- of 9

<strong>1.1                             Enter the data into </strong><strong>R </strong><strong>and re-produce the barchart (Figure 1).</strong>

Table 1 shows a summary of the data (it’s frequency table).

<ul>

 <li>Enter the data into R in an expanded form (long form) such that you will have a dataset with 1300 rows, of which, 630 will represent the Yes category and 670 represent the No category. <strong>Hint: </strong>Use existing R functions such as rep(), factor(), frame() or write your own function.</li>

 <li>Explore the data and produce a frequency table, by, for example typing tab1(binge) or summ() using the epiDisplay Reproduce the bar-chart below. Hint: tab1() will produces a bar chart for you with frequencies on the Y axis default. You can have percentages instead of frequencies by typing tab1(x, bar.values =”percent”.</li>

</ul>

Binge Drinking on Campus:

A Survey of N = 1300 Undergraduates

<strong>Figure 1: </strong>Barplots for drinking Binge

<h2>1.2             Chi-square Goodness of Fit Test</h2>

<ul>

 <li>To test if the proportion of Yes’s is significantly di erent from 0.5, we can type the following code: <strong>test(x=630, n=1300) </strong>or <strong>binom.test()</strong>. <em>What is your</em></li>

</ul>

<em>conclusion based on the output?</em>

<ul>

 <li>Perform a chi-square goodness of fit test to investigate the hypothesis that:

  <ul>

   <li>there is no di erence in proportion between the students who binge drink and <em><sub>your conclusion? </sub>” p</em>2. <em>What is </em>those that do not. That is, test that <em>H</em>0 : <em>p</em>1 = <em>p</em>2 versus <em>H</em>1 : <em>p</em>1 =</li>

   <li>the proportion of undergraduates on campus who binge drink <em><sub>fi </sub></em>= <em><sub>P</sub></em>(<em><sub>Y </sub></em>= <em><sub>yes</sub></em>) is di erent than the average reported by NSDUH: <em>H</em>1 : <em>fi </em>= 0<em>” .</em> The chi-square goodness of fit is testing whether the sample in hand appears to have been drawn from a population where the true rate of binge drinking is 0<em><sub>.</sub></em>247, or 24<em><sub>.</sub></em>7%. Note: we can verify the assumption that is based on sample size:0<em>.</em>247 <em>◊ </em>1300 = 321<em>.</em>1 and (1 5, that is (1 <em>≠ </em>0<em>.</em>247)<em>fi◊ n &gt;</em>1300 = 9785, that is,<em><sub>.</sub></em>9.</li>

  </ul></li>

</ul>

<em>What is your conclusion? ≠</em><em><sub>fi</sub></em>) <em>◊ </em><em><sub>n &gt;                                             </sub>◊</em>

<ul>

 <li>Since the administration of University A would only be concerned if the rate of binge drinking is high, we should really be focusing on evidence supporting rates that are higher than 24<em><sub>.</sub></em>7%. That corresponds to investigating the hypothesis <em><sub>H</sub></em><sub>1 </sub>: <em><sub>fi &gt; </sub></em>0 : 247. The <strong>binomial </strong>test is an exact test for one proportion that can be used when you your sample is too small to full fill the requirements of the chi-square goodness of fit test.</li>

</ul>

Perform both the <strong>Chi-square </strong>test and the <strong>binomial </strong>test. <em>What is your conclusion?</em>

<strong>prop.test</strong>(x = 630, n = 1300, p = 0.247, alternative = “g”) <strong>binom.test</strong>(x = 630, n = 1300, p = 0.247, alternative = “g”)

<h2>1.3        Sales Data</h2>

The CEO of Company Z is interested in learning more about sales patterns for the chain’s retail outlets across the United States. Tomorrow you have to let the CEO know whether the type of gear sold stores is associated with geographic location. For each store, you have information on the store’s geographic region (A, B, C, D) and its most popular type of sports gear sold (winter sports, summer sports, all-season sports; based on total sales volume) in the last three calendar years. The sales data is used to answer the questions that follow.

<ul>

 <li>Read in and examine the sales data. The summary table can be reproduced by typing</li>

</ul>

<strong>library</strong>(MASS)

(tabs &lt;- <strong>xtabs</strong>(<strong>~</strong>Region <strong>+ </strong>Sport, data = sales))

##     Sport

## Region A S W

##   A 9 6 22 ##    B 13 31 7 ##   C 7 15 0

##    D 14 13 13

<em># or tabpct(Region, Sport, graph=FALSE)</em>

<ul>

 <li>What is the distribution of most popular gear type within each region? To answer this question, What is the distribution of most popular gear type within each region? To answer this use prop.table() to generate a table of proportions and use the mosaic() to generate a mosaic question, produce a contingency table as shown below using tabpct() function from Then describe what you find.epiDisplay package or prop.table(), and mosaic() from <strong>vcd </strong>package.</li>

 <li>Perform a Chi-square test of independence to investigate the hypothesis that the sales of sports gear at a retail outlet is dependent on geographic region of the retail outlet. The only assumption we need to verify is based on sample size. None of the expected cell counts may be less than 5. The expected cell count for the cell in the <em><sub>i</sub></em>th row and <em>j</em>th column of the table can be calculated as:<em>j </em>(<em>C</em><em>i ◊ R</em><em>j</em>)<em>/N </em>where<em>N </em>is the overall sample<em>R</em><em>i </em>is the total count</li>

</ul>

for the <em>i</em>th row, <em>C </em>is the total count for the <em>j</em>th column, and

size. Based on the output of the chisq.test function, we should be able to check that we have su    cient numbers to use the chi-square test. <em>Do we? What is your conclusion</em>

<em>about the dependence of sales of sports gear on geographic region?</em>

<em># chisq.test(tabs) # Chi-square test</em>

<h1>2             Analysis of Continuous Outcome Data</h1>

<h2>2.1         One-Sample Tests</h2>

Fuel economy is measured under controlled conditions in a laboratory using a series of tests specified by federal law. Manufacturers test their own vehicles-usually pre-production prototypes-and report the results to the Environmental Protection Agency (EPA). EPA reviews the results and confirms about 15% to 20% of them through their own tests at the National Vehicles and Fuel Emissions Laboratory. Car Company A submitted to the EPA an estimate of 25 mpg (city and highway combined) for the fuel economy of their 2018 Sedan.

The EPA tested a random sample of 30 2018 Sedans to confirm the estimate submitted by Company A:

<table width="632">

 <tbody>

  <tr>

   <td width="632">car &lt;- <strong>c</strong>(19, 26, 24, 21, 24, 23, 26, 24, 23, 20, 21,24, 18, 21, 20, 23, 24, 26, 25, 19, 24, 23, 27,24, 26, 25, 20, 21, 19, 23)</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Perform a one-sample t-test to investigate the hypothesis that the average fuel</li>

</ul>

<em>conclusion? Produce a reasonable plot to visualize this single continuous outcome.</em>economy of the 2018 Sedan is not equal to 25 mpg (i.e., <em><sub>H</sub></em><sub>1 </sub>: <em><sub>µ </sub></em>= 25<em>” </em>). <em>What is your</em>

<em>Generate the mean and standard deviation of mpg</em>.

<em># t.test(car, mu=25)</em>

<ul>

 <li>The assumption of the t-test is approximate normality of the outcome. This assumption is not necessary for large samples, but since we’re dealing with 30 observations we need to check. Use the “eyeball” method with a normal Q-Q plot. A normal <strong>QQ plot </strong>is a scatterplot of the observed quantiles (percentiles) of the data against its expected quantiles assuming it follows a normal distribution. If normality is a reasonable assumption, the actual quantiles and the expected quantiles should be similar and thus follow a straight line. Use the <strong>Shapiro-Wilk </strong>test to assess normality. If the <em><sub>p</sub></em>-value is small (e.g., less than 0<em><sub>.</sub></em>05), it’s likely that the data have violated the normality assumption. Perform the <strong>Shapiro-Wilk </strong> <em>Does the data appear to follow the straight line?</em></li>

 <li>In general, we’re not concerned if our cars are getting better fuel economy than what is advertised. It makes sense in this situation then to focus our e orts on identifying whether Company A has overestimated the mpg of the 2018 Sedan (i.e., <em><sub>H</sub></em><sub>1 </sub>: <em><sub>µ &lt; </sub></em>25). Perform this one-sided test. Does it appear the cars are a random sample from a population of vehicles whose average mpg is less than 25? You should word your conclusion something like this: “There is su cient evidence to conclude that the average fuel economy of 2018 Sedans is less than the 25 mpg reported by Company A</li>

</ul>

(<em>p </em>= 0<em>.</em>03<em>,</em>95%<em>CI </em>: <em>UpperLimit</em>)”, OR “There is insu cient evidence to conclude that the average fuel economy of 2018 Sedans is less than the 25 mpg reported by Company A (<em>p </em>= 0<em>.</em>3<em>,</em>95%<em>CI </em>: <em>UpperLimit</em>)”

<em># t.test(car, alternative= less , mu=25)</em>

<h2>2.2          Dependent Samples Tests</h2>

The coach for the USA Swim Team is trying to identify training programs to improve the performance of athletes preparing for the 2016 Summer Olympics. A potential training program has been identified but must be tested on the athletes. To assess its e ectiveness, the coach will compare the times (in seconds) of 10 swimmers in the Men’s 1500 free-style prior to the training and their times after training:

<table width="632">

 <tbody>

  <tr>

   <td width="632">id &lt;- <strong>c</strong>(1<strong>:</strong>10)pre &lt;- <strong>c</strong>(899.63, 913.51, 897.05, 889.18, 903.2, 916.06,899.08, 892.75, 901.47, 902.63) post &lt;- <strong>c</strong>(899.53, 899.38, 879.25, 867.35, 897.97, 921.42,895.52, 893.95, 889.44, 898.14) datap &lt;- <strong>data.frame</strong>(<strong>cbind</strong>(id, pre, post))</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Install and load the PairedData package and produce a profile plot showing the paired di erences for each of the 10 swimmers.<strong>Hint: </strong>The first part of the code can be <strong>plotProfiles(datap, “pre”, “post”) </strong>+ <strong>geom_line(color=”blue”)</strong></li>

 <li>Recall that the coach wants to investigate the hypothesis that the training program is e ective in reducing swim times for male athletes in the 1500 freestyle; that is, whether or not swimmer’s times decrease under the new program (i.e.,(i) Generate the means and standard deviations of swim time pre- and post-training<em>H</em><sub>1 </sub>: <em>µ<sub>pre </sub>≠ µ<sub>post </sub>&gt; </em>0). and produce a boxplot showing the pre-and post-training distributions.

  <ul>

   <li>Compute the paired di erences and generate the mean and standard deviation of the di erences</li>

   <li>The assumption of the paired t-test is normality of the paired di erences. Use a normal <strong>Q-Q plot </strong>and the <strong>Shapiro-Wilk </strong>test to verify this assumption.</li>

   <li>Perform the t-test analysis for this paired data. What is your conclusion? Make sure you word it similar to: “There is su cient evidence to conclude that the training program is e ective at reducing swim times for Men’s 1500 Freestyle (<em><sub>p </sub></em>= 0<em><sub>.</sub></em>03). The program, on average, decreased swim time by 7 seconds (95% CI on di erence: <em>µ<sub>pre </sub>≠ µ<sub>post </sub>&gt; </em>0).”</li>

  </ul></li>

</ul>

<table width="632">

 <tbody>

  <tr>

   <td width="632"><em># Starting code </em>datap<strong>$</strong>diff &lt;- pre <strong>– </strong>post<strong>t.test</strong>(pre, post, paired = TRUE, alternative = “greater”)</td>

  </tr>

 </tbody>

</table>

<h2>2.3            Wilcoxon Signed-Rank Test</h2>

The Wilcoxon-Signed Rank test is a non-parametric test for comparing two dependent samples to assess whether their mean ranks di er. It’s a less powerful alternative to the paired t-test that should be substituted when the normality assumption cannot be verified or met. Perform the paired one-sided test using <strong>wilcox.test() </strong>function, with alternative = “greater” option. Does your conclusion di er from the paired t-test above?

<h2>2.4              Optional Question: One-Way ANOVA</h2>

Six di erent insect sprays are in development to help combat infestation of crops. Each of the 6 sprays were applied on 12 di erent fields and the number of insects found dead in the field was recorded. Researchers are interested in finding any significant di erences in e ectiveness across the six sprays. Load the data:

<strong>data</strong>(InsectSprays)

Recall that researchers want to investigate whether <strong>any di erence </strong>exists in the six insecticides under study. This hypothesis that we must nullify is called the <strong>omnibus null</strong>: <em><sup>H</sup></em><sup>0 </sup>: <em><sup>µ</sup></em><sup>1 </sup>= <em><sup>µ</sup></em><sup>2 </sup>= <em><sup>···</sup>µ </em><em><sup>µ</sup></em>=<sup>6 </sup>The alternative to this is that <strong>at least one of the insecticides is</strong>

with ANOVA, it is interpreted as<strong>di </strong><em><sub>i </sub>” µ<sub>j </sub></em>for some <em>i</em><strong>at least one of the means is di</strong>=<em>” j</em>). That is, if we find a statistically significant result<strong>erent</strong>. It alone can’t <strong>erent</strong>: <em>H</em><sub>1 </sub>:

tell us how many or which are di erent.

<ul>

 <li>Perform the one-way ANOVA to investigate the omnibus hypothesis. Graphically visualize the data. What’s the best graphic to visualize a continuous outcome across groups?</li>

 <li>Generate the mean and standard deviation of insect totals for each group using a function like <strong>tapply()</strong>, <strong>ddply() </strong>or <strong>numeric()</strong>.</li>

 <li>The assumptions of ANOVA are the same as the two-sample t -test: (1) normality of the outcome within each group and (2) equal group variances. To Check (1), assess the residuals for normality after fitting the ANOVA model. To check (2), use <strong>leveneTest() </strong>from the <strong>car </strong> Is ANOVA appropriate for this data? ANOVA is robust to violations of normality (especially for large sample sizes) but a violation of equal variances can severely impact our ability to make accurate inferences. The <strong>leveneTest </strong>is a formal test investigating the hypothesis that at least one of the group variances are unequal (i.e.,su <em>‡</em><em>i</em>2 =<em>” ‡</em><em>j</em>2 for <em>i </em>=<em>” j</em>). If you observe <em>p &lt; </em>0<em>.</em>05, you haveerent and the cient evidence to conclude that at least one of the variances are di</li>

</ul>

assumption is violated:

<table width="632">

 <tbody>

  <tr>

   <td width="632"><strong>library</strong>(car) <strong>data</strong>(InsectSprays)<strong>leveneTest</strong>(InsectSprays<strong>$</strong>count <strong>~ </strong>InsectSprays<strong>$</strong>spray)</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Use log transformation to transform the response variable count. Does it get better? <strong>attach</strong>(InsectSprays) countlog &lt;- <strong>log</strong>(count <strong>+ </strong>1) <strong>leveneTest</strong>(countlog <strong>~ </strong>spray)</li>

 <li>Fit the ANOVA with the log-transformed variable. Check for normality of the residuals. Do the residuals appear normally distributed?</li>

 <li>Since we have a significant di erence somewhere, it is important that we both identify it and describe it. Post-hoc comparisons can be performed using many methods, but an easy one to start with is Tukey’s Highly Significant Di erences (HSD) Test. It performs pairwise comparisons of all groups to find where any statistically significant di erences exist between groups. The output includes a table of all pairwise comparisons (e.g., ‘B-A’), an estimate of the di erence between the groups, and a confidence interval on the di erence. Which groups appear to be di erent?</li>

</ul>

<strong>TukeyHSD</strong>(fit)

<ul>

 <li>Perform a non-parametric Kruskal-Wallis Test. The Kruskal-Wallis test is analogous to the Mann-Whitney test for two groups. It is a robust (non-parametric) alternative to the one-way ANOVA that eliminates the need for normality and equal variances, but it also provides a less powerful test of di erences than ANOVA. Do the results of this test agree with the ANOVA from above?</li>

</ul>