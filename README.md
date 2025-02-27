# MEvA-LightGBM
A hybrid biomarker discovery tool based on combining a multi-objective Evolutionary algorithm and the LightGBM Classifier. It has been benchmarked on the Ornics dataset. With MEvA-LightGBM, the performance of the LightGBM Classifiers is enhanced, achieving better overall performance and/or the simplicity of the final models 

<h2>Flowchart</h2>
<img src="representation.png">

<h2>Details</h2>
<h4>About the algorithm:</h4>

 <table>
  <tr>
    <th>Python version</th>
    <th>3.9</th>
    <th>https://www.python.org/</th>
  </tr>
  </table>

<h4>Dependencies:</h4>
  <table>
  <tr>
    <th>Library</th>
    <th>Version</th>
    <th>Link</th>
  </tr>
  <tr>
    <td>Pandas</td>
    <td>1.4.4</td>
    <td>https://pypi.org/project/pandas/</td>
  </tr>
  <tr>
    <td>XGBoost</td>
    <td>1.7.3</td>
    <td>https://pypi.org/project/xgboost/</td>
  </tr>
 <tr>
    <td>LightGBM</td>
    <td>4.1.0.9.9</td>
   <td>https://lightgbm.readthedocs.io/en/stable/</td>
  </tr>
  <tr>
    <td>Numpy</td>
    <td>1.21.5</td>
    <td>https://numpy.org/</td>
  </tr>
  <tr>
    <td>Sklearn</td>
    <td>0.24.2</td>
    <td>https://scikit-learn.org/stable/</td>
  </tr>
  <tr>
    <td>mifs</td>
    <td>0.0.1.dev0</td>
    <td>https://github.com/danielhomola/mifs</td>
  </tr>
  <tr>
    <td>pickle</td>
    <td></td>
    <td>https://docs.python.org/3/library/pickle.html</td>
  </tr>
  <tr>
    <td>knnimpute</td>
    <td>0.1.0</td>
    <td>https://github.com/iskandr/knnimpute</td>
  </tr>
  <tr>
    <td>requests</td>
    <td>2.28.1</td>
    <td>https://pypi.org/project/requests/</td>
  </tr>
</table>

<h1> Tutorial </h1>
<p>A tutorial of how to use the tool in the form of a notebook can be found in the directory <code>Tutorial</code>.<br></p>

<h2>Example of calling MEvA-LightGBM from terminal:</h2>

<h4>Example of calling MEvA-LightGBM from terminal:</h4>
<p>This script is up and running and there is a detailed tutorial on the directory <code>Tutorial</code>.</p>

```
python MEvA-LightGBM.py --dataset_path ./Data/Ornish/diet_dataset.txt --labels_path ./Data/Ornish/diet_labels.txt --output_dir ./Data/Ornish/Results --K 5 --G 30 --P 60 --FS_dir ./Data/Ornish/FS_methods --goal_sig_path ./Data/Ornish/metrics_weights.txt --verbose False --plot False
```

<p>The parameters of the algorithm can be changed directly through the script in the __main__ section for the version V1.0.0.
 See in the table below the details for the parameters the user can experiment with:</p>

<h3>Parameters of the algorithm:</h3>
<table>
  <tr>
   <th>Parameter name</th>
   <th>Short description</th>
   <th>Default value</th>
   <th>Comment</th>
  </tr>
  <tr>
   <td>Population</td>
   <td>Number of individuals for the evolutionary algorithm</td>
   <td>50</td>
   <td>The higher the value the better the space can be explored but the slower the algorithm will get. <i>Advised values: 50-200</i> </td>
  </tr>
  <tr>
   <td>Generations</td>
   <td>Number of gererations the evolutionary will run for</td>
   <td>100</td>
   <td>The higher the value the better the further we allow the algorithm to explore, but the slower the algorithm will get overall. <i>Advised values: 50-200</i> </td>
  </tr>
  <tr>
   <td>dataset_filename</td>
   <td>Name of the data in the current directory</td>
   <td><i>None</i></td>
   <td>The dataset must be in the form of FeaturesXSamples in .txt, .csv, or .tsv format</i> </td>
  </tr>
  <tr>
   <td>labels_filename</td>
   <td>Name of the file that contains the labels of the datapoints</td>
   <td><i>None</i></td>
   <td>The labels must be in the form of an array with no labels</i> </td>
  </tr>
  <tr>
   <td>two_points_crossover_probability</td>
   <td>probability of the offsprings to be produced by the exchange of pieces from the parental individuals</td>
   <td>0.9 (90%)</td>
   <td>Controls what percentage of offspring will be the result of the crossover of its parental chromosomes. The higher the probability, the less conservative the solutions are (dependig on the similarity of the parental solutions). If it is used along with the <code>arithmetic_crossover_probability</code> their sum should not be greater than 1. <i>The recommended values are [0.75-0.95]</i></td>
  </tr>
  <tr>
   <td>arithmetic_crossover_probability</td>
   <td>probability of an arithmetic crossover of the parental individuals to produce the offsprings</td>
   <td>0.0 (0%)</td>
   <td>Controls what percentage of offspring will be the result of the crossover of its parental chromosomes. The higher the probability, the less conservative the solutions are (dependig on the similarity of the parental solutions). If it is used along with the <code>two_points_crossover_probability</code> their sum should not be greater than 1. <i>The recommended values are [0.0-0.1]</i></td>
  </tr>
  <tr>
   <td>mutation_probability</td>
   <td>probability of an offspring to mutate</td>
   <td>0.05 (5%)</td>
   <td>Control what percentage of offspring that will experience point mutations after their creation. The higher the probability, the more diverse the new population will be. <i>The recommended values are [0.03-0.1]</i></td>
  </tr>
  <tr>
   <td>goal_significances_filename</td>
   <td>array of weights for the objectives</td>
   <td>array of ones in the length of the objectives</td>
   <td>The weights must be in the form of an array with no labels</i> </td>
  </tr>
 <tr>
   <td>num_of_folds</td>
   <td>Number of folds for cross validation</td>
   <td>10</td>
   <td>The less the number of folds the more data the models are trained in each fold but the less certain we are for the robustness. <i>The recommended values are [5-15]</i> </td>
  </tr>
</table>

<h4>Calling the general version of the script</h4>

```
python MEvA-LightGBM.py
```

