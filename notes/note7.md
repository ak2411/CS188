# Decision Networks
## Anatomy of a Decision Network
* __Chance nodes__ - each outcome in a chance node has an _associated probability_, determined by running _inference_ on the underlying bayes' net it belongs to. (ovals)
* __Action nodes__ - nodes that _we_ have complete control over, i.e. we choose the action to take. (rectangle)
* __Utility nodes__ - children of a _combination of action and chance nodes_. They output a _utility_ based on the values taken on by their parents. (diamond)

## Calculating the MEU
* MEU - Maximum Expected utility
* The procedure:
  * instantiate all known evidence
  * run inference to calculate the _posterior probability_ of all the chance node parents of the utility node that's connected to the action node
    * basically the oval parents of the diamond who also has a rectangle parent
  * go through each possible action and compute expected utility:

    ![equation](http://www.sciweavers.org/tex2img.php?eq=EU%28a%20%7C%20e%29%20%3D%20%20%5Csum%5Climits_%7B%20x_%7B1%7D%2C%20...%20%2C%20x_%7Bn%7D%7D%20P%28%20x_%7B1%7D%2C%20...%20%2C%20x_%7Bn%7D%20%7C%20e%29U%28a%2C%20x_%7B1%7D%2C%20...%2C%20x_%7Bn%7D%29&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)

    action _a_, evidence _e_ and _n_ chance nodes, each x represents a value that the ith chance node can take on.
  * set the action which yielded the _highest utility_

## Outcome Trees
* root node maximizes expected utility, controlled by us
* action is selected from root and that takes us to the next level -  chance nodes
* chance nodes results in utility nodes with probabilities previously derived
* _difference_ with vanilla expectimax?
  * in outcome trees we annotate our nodes with what we know at any given moment (inside the {})

## Value of Perfect Information
* a mathematical quantification of the value an agent's MEU is expected to increase if it observes some new evidence.

  ![equation](http://www.sciweavers.org/tex2img.php?eq=MEU%28e%29%20%3D%20%5Cmax%5Climits_%7Ba%7D%20%5Csum%5Climits_%7Bs%7D%20P%28s%20%7C%20e%29U%28s%2Ca%29%20%5C%5C%0AMEU%28e%2Ce%27%29%20%3D%20%5Cmax%5Climits_%7Ba%7D%20%5Csum%5Climits_%7Bs%7D%20P%28s%20%7C%20e%2C%20e%27%29U%28s%2Ca%29%20%5C%5C%0AMEU%28e%2CE%27%29%20%3D%20%5Csum%5Climits_%7Be%27%7D%20P%28e%27%20%7Ce%29MEU%28e%2Ce%27%29%20%5C%5C%0AVPI%28E%27%7Ce%29%20%3D%20MEU%28e%2C%20E%27%29-MEU%28e%29%0A&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)
* new evidence e' before acting

## Properties of VPI
* __Nonnegativity__
  * Observing new information always allows you to make a _more informed_ decision so MEU can only _increase or stay the same_ (if info is irrelevant)

    ![equation](http://www.sciweavers.org/tex2img.php?eq=%20%5Cforall%20%28E%27%2C%20e%29%20VPI%28E%27%7Ce%29%20%20%5Cgeq%200&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)
* __Order-independence__
  * same gain in MEU regardless of the order of observing multiple new evidences.
  * makes sense - you don't take an action until you observe the evidences; you can observe all of them at the same time or in some arbitrary sequential order.

    ![equation](http://www.sciweavers.org/tex2img.php?eq=VPI%28E_%7Bj%7D%2C%20E_%7Bk%7D%7Ce%29%20%20%5Cneq%20VPI%28E_%7Bj%7D%7Ce%29%2BVPI%28E_%7Bk%7D%7Ce%29&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)
* __Nonadditivity__
  * generally observing some new evidence Ej might _change how much we care_ about Ek

    ![equation](http://www.sciweavers.org/tex2img.php?eq=VPI%28E_%7Bj%7D%2C%20E_%7Bk%7D%7Ce%29%20%3D%20VPI%28E_%7Bj%7D%7Ce%29%2BVPI%28E_%7Bk%7D%7Ce%2C%20E_%7Bj%7D%29%20%3D%20VPI%28E_%7Bk%7D%7Ce%29%2BVPI%28E_%7Bj%7D%7Ce%2C%20E_%7Bk%7D%29&bc=White&fc=Black&im=jpg&fs=12&ff=arev&edit=0)
