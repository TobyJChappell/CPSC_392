# Decision Trees
Decision trees are a classification model

When prompted with a question, classify/label based on answer.

## Example
If number of dogs < 5, adopt. Else if number of dogs >=5, do not adopt.

## Structure
First node is called a root node (does not have an input but has an output).

Internal nodes (have both an input and output).

Leaf nodes (have an input but not an output).

## Raw Data -> Decision Tree
Determine what the root node should be
- Find distribution of data for each column to predict goal
- Goal is to find distribution where there is a 0 (pure node)
    * In which, when making a decision, answer prompts only one answer
- Nodes that have distribution > 0 are called impure nodes

Calculate "impurity" value to determine which column should be root node
- Gini score = 1 - Σ(Pi^2) 
- Find weighted average of gini score's of each node to find "impurity"
- Column with lowest "impurity" is the node that should be root

Next goal is to determine where the tree splits using the same method.

### Example
Breakfast | Sleep | Generous Professor | Hours Studied | Passed
--- | --- | --- | --- | ---
Yes | No | Yes | 3 | No
Yes | No | Yes | 4 | No
No | Yes | No | 5 | Yes
No | Yes | No | 1 | Yes
Yes | Yes | Yes | 6 | Yes
No | No | No | 5 | No
Yes | No | Yes | 4 | Yes
Yes |Yes | Yes | 4 | Yes
No | No | Yes | 2 | No

Breakfast
- True:
    * Y: 3
    * N: 2
- False:
    * Y: 1
    * N: 3
- Gini score (left node) = 1 - ((3/(3+2))^2 + (2/(3+2))^2) = 0.48
- Gini score (right node) = 1 - ((1/4)^2 + (3/4)^2) = 0.375
- Weighted average = (5/(5+4))\*0.48 + (4/(5+4))\*0.375 = 0.43

Sleep
- True:
    * Y: 3
    * N: 1
- False:
    * Y: 1
    * N: 4
- Gini score (left node) = 1 - ((3/4)^2 + (1/4)^2) = 0.375
- Gini score (right node) = 1 - ((1/5)^2 + (4/5)^2) = 0.32
- Weighted average = (4/9)\*0.375 + (5/9)\*0.32 = 0.34

Professor
- Gini score = 0.48

Use sleep as root for decision tree

Sleep
- True:
    * Breakfast
        - True: 
            * Y: 2
            * N: 0
        - False:
            * Y: 1
            * N: 1
- Gini score (left-left node) = 1 - ((2/2)^2 + (0/2)^2) = 0
- Gini score (left-right node) = 0.5
- Weighted Average (left branch) = 0.25

Sleep
- True:
    * Professor
        - True: 
            * Y: 2
            * N: 0
        - False:
            * Y: 1
            * N: 1
- Gini score (left-left node) = 1 - ((2/2)^2 + (0/2)^2) = 0
- Gini score (left-right node) = 0.5
- Weighted Average (left branch) = 0.25

Since both give the same score, either one is valid.
- Choose Breakfast

Further split on breakfast to try to get pure nodes.

Sleep
- True:
    * Breakfast
        - False:
            * Professor
                - True:
                    * Y: 0
                    * N: 0
                - False:
                    * Y: 1
                    * N: 1

Will divide 0/0 meaning should not split with Professor

Sleep
- True:
    * Breakfast
        - True: 
            * Y: 2
            * N: 0
        - False:
            * Y: 1
            * N: 1
- False:
    * Breakfast
        - True: 
             * Y: 1
             * N: 2
        - False:
             * Y: 0
             * N: 2

## Tennis Dataset
Will a person play tennis depending on the weather.

Find root node

Outlook
- Sunny
    * Y: 2
    * N: 3
    * Gini Score: 1-((2/5)^2+(3/5)^2) = 0.48
- Overcast
    * Y: 4
    * N: 0
    * Gini Score: 1-((4/4)^2+(0/4)^2) = 0
- Rainy
    * Y: 3
    * N: 2
    * Gini Score: 1-((3/5)^2+(2/5)^2) = 0.48
- Gini Score: 5/14\*0.48 + 4/14\*0 + 5/14\*0.48 = 0.3429

Temperature
- Cold
    * Y: 3
    * N: 1
    * Gini Score: 1-((3/4)^2+(1/4)^2) = 0.375
- Mild
    * Y: 4
    * N: 2
    * Gini Score: 1-((4/6)^2+(2/6)^2) = 0.4444
- Hot
    * Y: 2
    * N: 2
    * Gini Score: 1-((2/4)^2+(2/4)^2) = 0.5
- Gini Score: 4/14\*0.375 + 6/14\*0.4444 + 4/14\*0.5 = 0.4405

Humidity
- Normal
    * Y: 6
    * N: 1
    * Gini Score: 1-((6/7)^2+(1/7)^2) = 0.2449
- High
    * Y: 3
    * N: 4
    * Gini Score: 1-((3/7)^2+(4/7)^2) = 0.4898
- Gini Score: 7/14\*0. + 7/14\*0. = 0.3673
 
Windy
- True
    * Y: 3
    * N: 3
    * Gini Score: 1-((3/6)^2+(3/6)^2) = 0.5
- False
    * Y: 6
    * N: 2
    * Gini Score: 1-((6/8)^2+(2/8)^2) = 0.375
- Gini Score: 6/14\*0.5 + 8/14\*0.375 = 0.4386

Select Outlook as root

Find split at Sunny

Outlook
- Sunny
    * Temperature
        - Cold
            * Y: 1
            * N: 0
            * Gini Score: 0
        - Mild
            * Y: 1
            * N: 1
            * Gini Score: 0.5
        - Hot
            * Y: 0
            * N: 2
            * Gini Score: 0
     * Gini Score: 0 + 2/5\*0.5 + 0 = 0.2

Outlook
- Sunny
    * Humidity
        - Normal
            * Y: 2
            * N: 0
            * Gini Score: 0
        - High
            * Y: 0
            * N: 3
            * Gini Score: 0
     * Gini Score: 0 + 0 = 0

Outlook
- Sunny
    * Windy
        - True
            * Y: 1
            * N: 1
            * Gini Score: 0.5
        - False
            * Y: 1
            * N: 2
            * Gini Score: 0.4444
    * Gini Score: 2/5*\0.5 + 3/5\*0.4444 = 0.4667

Select Humidity to branch off of Sunny

Find split at Rainy

Outlook
- Sunny
    * Humidity
- Overcast
- Rainy
    * Temperature
        - Cold
            * Y: 1
            * N: 1
        - Mild
            * Y: 2
            * N: 1
        - Hot
            * Y: 0
            * N: 0

Temperature invalid split (cannot divide by 0)

Outlook
- Sunny
    * Humidity
- Overcast
- Rainy
    * Humidity
        - Normal
            * Y: 2
            * N: 1
            * Gini Score: 0.4444
        - High
            * Y: 1
            * N: 1
            * Gini Score: 0.5
    * Gini Score: 3/5\*0.4444 + 2/5\*0.5 = 0.4667

Outlook
- Sunny
    * Humidity
- Overcast
- Rainy
    * Windy
        - True
            * Y: 0
            * N: 2
            * Gini Score: 0
        - False
            * Y: 3
            * N: 0
            * Gini Score: 0
    * Gini Score: 0
    
Select Windy to Branch off of Rainy

Final Decision Tree:

Outlook
- Sunny
    * Humidity
- Overcast
- Rainy
    * Windy