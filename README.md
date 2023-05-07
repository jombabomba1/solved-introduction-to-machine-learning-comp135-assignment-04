Download Link: https://assignmentchef.com/product/solved-introduction-to-machine-learning-comp135-assignment-04
<br>
For this assignment, you will be exploring the use of some neural network models—also known as multi-layer perceptron (MLP) models—on some supplied data. The data is laid out in what is known as the XOR pattern, with classes that cannot be separated by any technique like logistic regression using solely linear functions on the data, but which can be handled using a neural network classifier with a single hidden layer:

Along with this document, you are provided with:

<ul>

 <li>A Python notebook in which to do all your work; you will submit this notebook, along with the usual collaborators file, and you will also submit a PDF generated from the final version of your notebook.</li>

 <li>Some Python utility files that will be called upon by your notebook to do some of the visualization work, and provide a better interface to some model internals (place them in the same directory as the notebook when working on your code).</li>

 <li>Data-files in the usual CSV format for inputs/outputs of a training and test set. Each input data-point has two features, <em>x</em><sub>1 </sub>and <em>x</em><sub>2</sub>, and output labels are either 0 or 1.</li>

</ul>

Your code will examine different optimization algorithms for learning neural network weights (designated by the solver parameter in sklearn models), as well as different activation functions (activation in sklearn).

<strong>Optimization</strong>: You will compare:

<ul>

 <li><strong>SGD </strong>(stochastic gradient descent): a standard form of weight propagation using the first derivative of the network loss, with the gradient approximated each iteration using a subset of the data-set.</li>

 <li><strong>L-BFGS </strong>(limited-memory Broyden-Fletcher-Goldfarb-Shanno): a more complex method using both the first and second derivatives.<sup>∗</sup></li>

</ul>

∗

This method is explained in some detail at the following link (understanding all the details is beyond the scope of this class, and not necessary for completion of the assignment, but the information is provided for those who are interested): <a href="http://aria42.com/blog/2014/12/understanding-lbfgs">http://aria42.com/blog/2014/12/understanding-lbfgs</a><a href="http://aria42.com/blog/2014/12/understanding-lbfgs">.</a>

<strong>Activation</strong>: You will compare two functions, both seen in class:

<ul>

 <li><strong>ReLU </strong>(rectified linear unit): a simple piece-wise linear activation function, popular in many modern applications.</li>

 <li><strong>Sigmoid</strong>: the traditional logistic Sigmoid activation function, historically one of the most popular (and the same non-linear function as used for logistic regression, but put to quite a different use in the neural network context).</li>

</ul>

<h1>Code completion (26 points)</h1>

<ol>

 <li>(<em>4 pts.</em>) Use the provided class MLPClassifierWithSolverLBFGS, which is a wrapper around the sklearn<a href="https://scikit-learn.org/stable/modules/generated/sklearn.neural_network.MLPClassifier.html">MLPClassifier</a> model, but which provides more convenient access to some of its internal features. The class is fully described in its source-code. You will be building models with two hidden nodes that use the <em>ReLU </em>activation, and optimizing using <em>L-BFGS</em>.</li>

</ol>

Train 16 separate such models, each one using a different random initialization-state; to do so, each model should be built with random_state set to 0<em>,</em>1<em>,</em>2<em>,…,</em>15, in order. (The supplied code already builds the first of these, you just need to modify it to create and store the remaining models.)

<ul>

 <li>Plot a 2D visualization of the learned decision boundaries for each of the 16 models.</li>

 <li>What fraction of the runs achieve 0 error? What happens in other cases, and why do you suppose this is? How long, on average, does it take the models to converge?</li>

</ul>

<ol start="2">

 <li>(<em>4pts</em>) Repeat the process to build 16 randomized models, each of which combines the <em>logistic Sigmoid </em>activation with the <em>L-BFGS </em> Again, plot each of the decision boundaries, and analyze the performance just as before.</li>

 <li>(<em>6 pts</em>) Use the default sklearn MLPClassifier model, with the <em>ReLU </em>activation, but trained using <em>SGD</em>. Again, you should build 16 models with random seeds in 0<em>,</em>1<em>,…,</em>15, setting up the models to do stochastic gradient descent as follows:

  <ul>

   <li>solver=’sgd’</li>

   <li>batch_size=10</li>

   <li>max_iter=400</li>

   <li>tol=1e-8</li>

   <li>learning_rate=’adaptive’</li>

   <li>learning_rate_init=0.1</li>

   <li>momentum=0.0</li>

  </ul></li>

</ol>

That is, your models use 10 training examples per weight update step, for 400 total passes through the data, stopping early only if loss values change by no more than the tolerance (tol), and modifying the learning rate as it goes.<sup>†</sup>

Again, plot the decision boundaries learned by each of the 16 models, and analyze the performance rates as before. In addition, discuss the difference between the results you see

†

Fuller discussion of SGD can be found at <a href="https://scikit-learn.org/stable/modules/sgd.html">https://scikit-learn.org/stable/modules/sgd.html</a><a href="https://scikit-learn.org/stable/modules/sgd.html">.</a>

here and those from the first set of models, which also used the ReLU activation, but optimized differently—what are the most noticeable differences between the runs, and why do you suppose this happens?

<ol start="4">

 <li>(<em>6 pts.</em>) Repeat the process of the last step, again using <em>SGD</em>, but using the <em>logistic </em>for activation. Again, plot the results, analyze them, and then compare these results to the ones using L-BFGS with the logistic.</li>

 <li>(<em>6 pts.</em>) You will now analyze the loss curves of the various model runs already completed. Each such curve can be accessed via the loss_curve attribute of an MLP classifier model for analysis and plotting.

  <ul>

   <li>Plot the loss curves for each of the four groups of models in a (2×2) grid, so each panel will contain the curves for all 16 of the relevant models.</li>

   <li>Based upon these plots, and the ones you made in prior steps, which activation function seems easier to optimize? Which requires the most iterations in general?</li>

   <li>Does it appear convincing that one of the activation functions is simply easier to optimize than the other? What are three more experiments we could conduct that would help us establish if this is generally true?</li>

  </ul></li>

</ol>

<h1>Code submission (4 points)</h1>

<ol>

 <li>(<em>2 pts.</em>) Submit the source code (ipynb) to Gradescope.</li>

 <li>(<em>2 pts.</em>) Along with your code, submit a completed version of the txt file.</li>

</ol>

An example has been provided, which you should edit appropriately to include:

<ul>

 <li>Your name.</li>

 <li>The time it took you to compete the assignment.</li>

 <li>Any resources you used to complete the assignment, including discussions with the instructor, TA’s, or fellow students, and any online or offline resources consulted. If you did not need to consult any outside resources, you can say so.</li>

 <li>A brief description of what parts, if any, of the assignment caused you to seek help.</li>

</ul>

<strong>Submission details</strong>: Your work should satisfy the following requirements:

<ul>

 <li>Your code must work properly with the versions of Python and other libraries that are part of the COMP 135 standard environment. The class website contains instructions for installing and using this environment.</li>

</ul>

<a href="http://www.cs.tufts.edu/comp/135/resources/">http://www.cs.tufts.edu/comp/135/resources/</a>

You can write the Python code using whatever tools you like, but you should ensure that the code executes properly.

<ul>

 <li>There are two Gradescope submission links for this assignment. You will upload the following:</li>

</ul>

<ul>

 <li><strong>Code</strong>: Submit the completed notebook source (i.e., the ipynb file, along with the COLLABORATORS.txt file. Grading will be based upon submission of both files.</li>

 <li><strong>PDF</strong>: Generate a PDF from your notebook (you can do this simply by printing it to a PDF from your web browser, or exporting it via the Jupyter functionality for doing that). Submit the PDF at the relevant link for grading.</li>

</ul>