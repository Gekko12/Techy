# #################################### #
#     Statistics and Probability       #
# #################################### #

- Statistics is the art of learning from data.
- It involves data collection, describing it, analysis, and ultimately drawing conclusions.
- Statistics can be classified as:
    1. Descriptive (like central tendency, avg/mean, mode, median, provides summary statistics of data)
    2. Inferential (makes inferences about the properties of a population)
- Central tendency is a statistic that represents the single value of the entire population or a dataset. Some of the important examples of central tendency include mode, median, arithmetic mean and geometric mean, etc.
- The study of statistics revolves around datasets. Datasets can be either of the following:
    1. Population: includes all the elements in a dataset.
        Example: Collection of persons, things, or objects.
    2. Sample: consist of one or more observations drawn from a population (subset of population).
        Example: Students of Class X in a school.
- Probability is the likelihood or chance of an event happening.
- Every experiment starts with Data Collection, followed by Data Analysis.
- Data Analysis is the process of applying logical or statistical techniques to evaluate and describe data in a meaningful way.
- Descriptive Statistics - Measures
    + Measures of Central Tendency: Focus on the average or central point of a dataset.
        1. Mean
        2. Median
        3. Mode
    + Measures of Spread: Focus on the dispersion of data from the central point.
        1. Range
        2. Standard Deviation
        3. Variance
        4. Interquartile Range
- Inferential Statistics - Terms
    1. Estimation: Process of analyzing the parameter of population.
    2. Point Estimation: Single value that determines the parameter of population.
    3. Confidence Intervals: Range of values within which the parameter is included.
    4. Hypothesis Tests: Specific values of the parameter are tested.
- Estimation: In this process, a sample is drawn from a population to estimate the following:
    1. Parameter: Mean, Standard Deviation, Proportion, Correlation.
    2. Confidence Interval: Range of values of an unknown population parameter.
- Hypothesis Testing: A hypothesis test helps in determining whether to reject or retain a claim about a population, depending on the evidence provided by a sample of data.
- Descriptive vs Inferential
    + Descriptive Statistics:
        * Describes target population.
        * Analyzes and presents data in a meaningful manner.
        * Conclusions are represented by forms, charts, and so on
        * Tools: Measures of Central Tendency- Mean, Median, Mode.
    + Inferential Statistics:
        * Produces inferences from samples.
        * Predicts the future.
        * Conclusions are represented by probability scores.
        * Tools: Hypothesis Test.
- Permutation/Arrange order matters, same not true for Combinations/Select.
- Interquartile Range:
    2,5,9,11,13,20,56,60,60 (sort required)
    median = 13
    median of first half = [2,5,9,11] => (5+9)/2 => 7
    median of second half = [20,56,60,60] => sum(56+60)/2 => 58
    So, IQR = 58 - 7 => 51
- Experiment: a procedure that can be repeated infinetly, resulting a set of possible outcomes.
- Sample Space: set of all possible outcomes of an experiment.
- The value of probability lies b/w 0 and 1.
- Elementary/Simple Event: event containing a single element of a sample space. Eg getting 1 on a die
- Compound Event: event containing two or more element of a sample space. Eg getting even num on a die
- Dependent Event: if the occurence of one event is influenced by another event. Eg. if die got odd num, we toss the coin
- Independent Event: vice-versa
- Exhaustive Event: set of events that devour the entire sample space. Eg getting a num on die
- Mutually Exclusive: when both event cannot occur at the same time. Eg getting even and odd number on die in a single throw P(A U B) = P(A) + P(B)
- Non-mutually exclusive: getting prime and even number in a die, as 2 is prime as well as odd <= P(A union B) = P(A) + P(B) - P(A intersection B) <= 3/6 + 3/6 - 1/6
- Binomial Distribution:
    P(x, n, p) = nCx * p^x * (1-p)^(n-x)
    where n = number of trials,
          p = probability of success,
          x = number of success which can occur anywhere among thround(e n trials
- Poisson Distribution
- Joint Probability is a measure of two events happening at the same time, and can only be applied to situations where more than one observation can occur at the same time. P(A and B)
- Conditional Probability: The probability of an event ( A ), given that another event ( B ) has already occurred ie. P(A|B) or P(A, given B)
- P(A|B) = P(A inter B) / P(B)
- Independent Event, P(A|B) = P(A), P(B|A) = P(B)
- Naive Bayes theorem, P(Y|X) = P(X|Y)*P(Y)/P(X) formed using P(X inter Y) = P(X|Y)P(Y) and P(Y inter X) = P(Y|X)P(X)
- A random variable represents the outcome of statistical experiments on numerical values.
- Consider the experiment of tossing a coin, where the result could either be heads or tails.
    Assume that the values are:
        Heads = 0
        Tails = 1
    X will be the random variable denoting the outcome of tossing the coin.
        X= {0,1}
- Random variable can be discrete or continous
- When a probability function is used to describe a discrete probability distribution, it is called Probability Mass Function (PMF). 
- A continuous form of PMF is PDF (Probability Density Function).
- Continuous Random Variable: The Cumulative Distribution Function (CDF) of a continuous random variable X can be expressed as the integral of its probability density function fx
- The Central Limit Theorem (CLT) states that the sampling distribution of a sample mean approaches a normal distribution, as the sample size gets larger.
- Consider a population with:
    * Mean μ
    * Standard Deviation σ
take sufficiently large random samples from the population with replacement, then the distribution of the sample mean will be approximately normally distributed.
- This will hold true regardless of whether the source population is normal or skewed, provided the sample size is sufficiently large (usually n > 30).
- Var [aX + b] = a^2 V[X]
- The following are the most commonly used Discrete Distribution Functions:
    1. Binomial probability distribution
    2. Poisson probability distribution
    3. Hypergeometric probability distribution
    4. Multinomial probability distribution
    5. Negative binomial distribution
- The following are the most commonly used Continuous Distribution Functions:
    1. Normal/Gaussian distribution  
    2. Uniform distribution
    3. Chi-squared distribution
    4. F distribution
    5. t distribution
+ Kernel are like small func whose values can be found only within the interval. Outside the interval, its value becomes zero. 
+ Use of only one variable to describe the data is known as Univariate data analysis. 
+ Use of two variables to describe the data and finding out the relationship between them is known as bivariate data analysis.
+ Multivariate Data Analysis consists mainly of three phase which we will explore in details:
    1. Categorization of variables
    2. Dimensionality reduction
    3. Cause-effect relationship
+ A multivariate random variable is a set of unknown variables. The value of variable is unknown because of its non occurence or the value is still unclear.
+ Which fields are using multivariate statistics?
    * It is being widely used in Pharmaceuticals to study several drugs together.
    * In Medical science, it is used to study several readings from human body
    * Climate and weather study requires analyzing several variables together
+ Simpson's Paradox: Sometimes, having a multivariate analysis produces a misleading result because of some lurking variables that is left unanalysed but seriously affects the relationship in between analysed variables. 
+ "Lurking variable" takes its name from the word lurk which means remaining hidden waiting for something to happen!
+ Classification of Multivariate Analysis Methods
    1. Multivariate analysis in which relationship exist between a dependent variable and independent variable/s. For example: Partial least squares regression, Multiple Regression Analysis, Multiple discriminant analysis etc. 
    2. Multivariate analysis in which no defined relationship exist in between dependent variable/s and independent variable/s. For example: Cluster analysis etc. 
+ Regression analysis can be thought of a mathematical technique of sorting and deciding which of the variables in the analysis puts how much impact on the result! It also describes how the variables interact with each other. 
+ Least square means fitting the regression line by minimizing the sum of squares of the distance between the actual and predicted values. 
+ The goal of Partial least square regression is to determine dependent variables from independent variables (also known as predictors). In statistical terms, it can be said that we predict Y from X.
+ Principal component analysis is a type of Multivariate data analysis for reducing large number of corelated variables into set of values of un-corelated variables. It is also known as Principal mode of variation.
+ Let us discuss Principal component analysis with an example:
    * A research firm decides to perform Principal component analysis on a Mars rover being designed by them! Following Characteristics are studied : 
    * A. Speed and acceleration B. Recharge time C. Power consumption D. Solar recharge time E. Brake power and deceleration
    * Since it is difficult to analyse all the variables at once, they want to sort them to a smaller number of uncorrelated variables. Hence,they find that characteristics like A and E can be studied as a single component Velocity. Similarly, B,C and D can be studied as Battery life. Now we have only two components to analyse. This is the main goal of Principal component analysis. 26 Principal component analysis preserves the essence of original data while compressing it just like the television which instead of having two dimensional screen, can represent a three dimensional data without information loss!
+ Random Variable
    * Random variables are possible numerical values of the outcome of an experiment!
    * It is denoted by X.
    * It is also known as stochastic variable.
    * Can be discrete or continuous
+ Probability Mass Function: function giving the probabilities of discrete random variables.
+ The cumulative distribution function for continuous random variables is the more natural function as most of the time, our dataset is continuous in nature! Hence, we replace the summation by integral.
+ A parameter is a measurable quantity telling something useful about the population! Ex: mean, median, mode, standard deviation etc.
+ Note: Do not confuse parameter with variables!
+ Number of variable is decided by us during the experiment whereas, number of parameters remains constant. 
+ Estimation is related with the estimation of parameters. It is some conclusion that we can draw from the population.
+ Estimation can be subdivided as:
    1. Point estimation: estimation that can be represented as single value.
    2. Interval estimation: estimation can be represented with two numbers which acts as the interval of the maybe values of the unknown parameter.
+ Density estimation is a statistical process of the estimation of probability density function of a population present in the observation set.
+ Prior Probability:
    * As the name suggests, we can say something in general about the event before we have data related to it. 
    * When the probability distribution of the uncertain quantity is done in the absense of data 1.e. lack of the evidence, then it is called prior probability distribution or simply prior. 
    * For example, Finding the probability distribution of persons attending the wedding party after the invitation is sent can be called as prior probability.
+ Posterior probability of the random event can be said as the conditional probabilty of the event after the evidence is taken into the consideration! It is the probability distribution of the unknown quantity which depends on the evidence from the experiment.
+ Markov process is a random process in which past event not affects future event if we have the knowledge of present event! Hence, the prediction about the future process can be done by knowing the present state.