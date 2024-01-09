![[T11_2023_students.pdf]]

## Summary
* **Recommendation techniques**
	*  *Knowledge-based* methods go to the root of the decision problem 
	* *Collaborative-based* methods are the most popular 
		* Suffers from bootstrapping problems 
	* *Content-based* methods are well rooted in information retrieval 
	* *Hybrid methods* are the most powerful and popular right now 
* *Collaborative Filtering*
	- *Basic Concept*: Relies on the opinions and behaviors of similar users to make recommendations. It filters items by evaluating how other users have interacted with them.
	- *Types*: Includes user-based filtering, which recommends items liked by similar users, and item-based filtering, recommending items similar to those the user has previously liked.
* *Content-Based Recommenders*
    - *Approach*: Focus on item features similar to those liked by the user in the past, using information retrieval methods.
    - *Functionality*: Analyzes item descriptions and user profiles to suggest items based on similarity comparison and user interest history.
- *Conversational Recommenders*
    - *Interactive Process*: Guides users through suggestions and feedback, adapting future suggestions based on user input.
    - *Feedback Mechanisms*: Includes value elicitation, preference-based feedback, and critiquing, enabling tailored recommendations.
- *Outside Recommenders*
    - *Personalized Algorithm*: Generates tailored recommendations based on user interactions and preferences.
    - *Application Diversity*: Extends to various domains like 3D virtual worlds and cognitive assistants, enhancing user experience across different platforms.
## Notes
### Introduction to Recommender Systems
* *Internet = information overload*
	* Too *much information complicate to take a decision*
	* *Information retrieval*: helps to locate content
* *Recommender systems*: help to make choices without personal experience of the alternatives
	* *Suggest products* to customers
	* To do this we need technology to *filter*, *search*, *rank*
		* This technology includes: *machine learning*, *adaptative and personalized system*, *user modelling*, *intelligent user interfaces*, etc...
* Many top technology companies use Recommender systems
* *The recommendation process*
	* User input preferences $\rightarrow$ receives recommendations $\rightarrow$ decides if accept the recommendation or not
	* Users want
		* *Fast*, *Engaging*, and *Easy* process
		* *Good*, *New* recommendations
* *Objective of RS*
	* Help people to *make decisions* (when user asks)
	* Help to *maintain awareness* (even if user doesn't asks)
* Recommender systems are a specific type of *information filtering* technique that attempt to present to the user information *items* (movies, music, books, news, web pages) *the user is interested in*. To do this the *user's profile* is compared to some reference characteristics
* An important part in the process is to be able to **compute similarity between objects**
	* *User-user* (*users profiles*)
	* *item-item*
### Recommendation techniques
* *Types of recommenders*
	* *Single recommenders*: one user - one product
	* *Group recommenders*: Several users- one product (user interact with members for making a choice)
		* Address recommendations to groups of users
			1. identify user's individual preferences
			2. Find a compromise that is fair and acceptable to all the users
* *Recommendation techniques*
	* *Knowledge-based (KB):* knowledge about users and products using discrimination: *Decision trees*, *decision rupport tools*, *case based reasoning*
		* Data from:
			* Domain knowledge, product features, user’s need/query 
			* Inferences about user’s needs and preferences
	* *Collaborative Filtering (CF):* preferences and *recommendations* to other users based on *similarity in behavioral patterns*
		* Data from:
			* Users ratings
	* *Content-based:* supervised machine learning to classify between *interesting*/*not interesting* for a user
		* Product features, user’s ratings 
		* Classifications of user’s likes/dislikes
	* *Hybrid Filtering techniques:* combination of the techniques above
* *Context-aware recommender systems*
	* Use additional users information (maybe not directly relevant) when computing recommendations 
	* *Obtaining contect*
		* User provided
		* Observed/deduces by the system
		* Deduced from user behaviour
* *Weakness in recommender systems*
	* *Cold start problem:* cannot draw *inferences* for *new users*
	* *Latency problem*: new items incorporated into a RS cannot be used in CF (collaborative) recommendations before a substantial amount of users have evaluated it
	* *Sparcity problem:* few users have rated the same items
	* *Gray-sheep problem*: users that fall on the borders between groups of users
* **Components of a recommender**
	* ![[Pasted image 20240108172636.png|500]]
* 
### An overview of collaborative filtering
* *Sources of recommendation*
	* ${p1, p2}$ People with similar profiles
		* $p1$ has a new preference object $o$ $\rightarrow$ recommend $o$ to $p2$
	* $o1,o2$ are similar objects
		* User $p$ has a preference over $o2$ $\rightarrow$ recommend $o1$ to $p$
* *Collaborative filtering* (One of the most used)
	* Process of *filtering or evaluating* items through the *opinions of other people*
		* Maintain a database of many users’ ratings of a variety of items
		* For a given user, find other similar users whose ratings strongly correlate with the current user
		* ![[Pasted image 20240108173342.png|400]]
* *Types of Collaborative Filtering*
	* *User-based*: Looks at *profiles of “similar” users* and recommends their most frequently selected or *highest-ranked items*
		* *Similarity between users*
			* *Cosine based*
			* *Correlation based*
	* *Item-based*: Looks at *“similar” items* and *recommends* those most frequently selected or *highest-ranked*
		* *Rating predictions*
			* Recommend to $u$ items “similar” to those best ranked by $u$
		* *Similarity between items*
			* *Cosine*
			* *Pearson*
			* *Adjusted cosine*
### An overview of content-based recommenders

- Based on the **conjecture** that a *person likes items with features similar to* those of other *items he/she liked in the past*
- Closely related to *Information Retrieval* 
- *Takes in to account*
	- **Describing items**
		- *CF* (collaborative filtering) doesn´t use *information about the items*, but it is used in *Content-Based*
		-  *Information* from *items*
			- Class
			- Genre
			- Description, etc...
	- **Creating a profile**: 
		- The profile is created and updated automatically using *feedback* on the desirability.
		- A *user profile* contains information about the *user’ tastes*, *interests* and *needs*
		- A *comparison between their content and the user profiles* 
	- **Comparing items**
- **Content-based recommender**
	- Looks at *items of "similar" content-based features*
	- *Analyse items description*
	- *Items suggested* according to  *descriptions similarity comparison* and comparison to users profile.
	- *Representation of items
		- *Database Table*
		- *Unstructured data*: news, articles
		- *Semi-structured data*: attributes with restricted values
	- *User profiles*:
		- *User interests*
		- *History of the user's interactions*
		- *Learn a user model:* Learn user preferences using user history
	- *Advantages*
		- No need for data of other users
		- No cold-start or sparsity problems
		- Able to recommend new and unpopular items
		- *Transparency*: can explain recommendations
	- *Disadvantages*
		- *Requires content analysis*: the effectiveness *depends on the available descriptive data*
		- *Content-overspecialization:* it only retrieves items that score highly against a specific user profile
		- *Portfolio-reflect*: the user should be presented with a diverse range of options
### Conversational recommenders
- *Guide the user* through a complex problem space by *alternatively making suggestions* and *using user feedback to influence future suggestions*.
- USE of CBR: Items are retrieved using similarity measures
	- ![[Pasted image 20240108200000.png|200]]
- *Forms of feedback*
	- *Value elicitation*: *ask the user to provide details* relating to specific features 
	- *Preference-based feedback and Rating- based*: *ask the user to indicate which product* they *prefer* when presented with a small set of alternatives 
	- *Critiquing or tweaking*, the *user expresses a directional preference over the value-space* for a particular product feature
		- “FindMe Systems”
		- Basic Assumption
		- Practical Applications
- After the first search if the results are not satisfactory, their user expreses their restrictions (critiques) ---> *"more like this but cheaper”*
- *Advantages* 
	- No ratings are necessary 
	- Avoid cold start problem 
- *Limitations* 
	- cost of knowledge acquisition 
	- from domain experts 
	- from users 
	- from web resources 
	- accuracy of preference models 
	- very fine grannular preference models require many interaction cycles
### Outside recommenders
- *An algorithm that generates* **personalized recommendations**
	- ![[Pasted image 20240108200416.png|400]]
- Recommenders need an *interface for capturing user’s interactions and preferences
- *Types of outside recommenders*
	- *3D Virtual Worlds*: Design a SCALABLE framework to enhance and facilitate user buying experience in a large 3D eCommerce space
	- *Cognitive Assistants* 
	- *gCoach: Collaborative Group Recommender*