[//]: # (Styles:)

[//]: # (<style>)

[//]: # (.center {)

[//]: # (  display: block;)

[//]: # (  margin-left: auto;)

[//]: # (  margin-right: auto;)

[//]: # (  width: 70%;)

[//]: # (})

[//]: # (</style>)


[//]: # (Actual Github Page:)

<h1>BCI - Emotion - Classification </h1>

<p> <strong>Authors:</strong> Ernesto, Alex, Novo</p>

<h2>Introduction</h2>

In this project we replicated the data preprocessing of 3 emotional states (concentrated, relaxed, and neutral states)
obtained from the Dataset
used by Jordan et. al in "A Study on Mental State Classification using EEG-based Brain-Machine Interface". We
demonstrate that it is possible
to achieve a high classification accuracy using his preprocessing technique which consists in creating a defined set of
statistical features
plus FFT windows based on 4 channels with the commercial Muse EEG headband.

Furthermore, we also download a special dataset named Seed IV, and try to replicate the findings in this new dataset.


<p> Credits:</p>

<p> Dataset and Papers based on Jordan's dataset:</p>
<ul>
    <li>
    <a href="https://github.com/jordan-bird/eeg-feature-generation">Jordan-bird/eeg-feature-generation</a>
    </li>
    <li>
    <a href= "https://ieeexplore.ieee.org/abstract/document/8710576"> 
                Paper: A Study on Mental State Classification using EEG-based Brain-Machine Interface</a>
    </li>
    <li>
    <a href= "https://www.hindawi.com/journals/complexity/2019/4316548/"> 
                Paper: A Deep Evolutionary Approach to Bioinspired Classifier Optimisation for Brain-Machine Interaction</a>
    </li>
    <li>
    <a href= "https://www.researchgate.net/publication/329403546_Mental_Emotional_Sentiment_Classification_with_an_EEG-based_Brain-machine_Interface"> 
                Paper: Mental Emotional Sentiment Classification with an EEG-based Brain-machine Interface</a>
    </li>
</ul>


<h2>Dataset</h2>

<h3>Jordan-Bird et. al Dataset</h3>

In Jordan J. Bird's research, he and his team based themselves on trying to classify mental activity into relaxing,
neutral, and concentrating states.
They used the commercially available Muse headband, to focus on 4 EEG Sensors: (TP9, AF7, AF8, and TP10). Theses 4
channels were selected because past research
states that they are the good indicators of this mental activity, and also because of the easier availability for the
general public to get hold of one of these
devices. They have gathered the data and features from several experiments, but the latest one is from "A Study on
Mental State Classification using EEG-based Brain-Machine Interface":


<figure class="center">
  <img src="Pictures/4_channels_used.png" alt="Channels used" >
  <figcaption>EEG sensors TP9, AF7, AF8 and TP10 of the Muse headband</figcaption>
</figure>
<br><br>

For the data collection process, they utilized the commercially available MUSE band, which has 5 electrodes (1 being the
reference, NZ).
They made 3 types of stimuli corresponding for 3 types of mental states (relaxed, neutral, concentrated). For the
relaxed stimuli,
they made the participants hear calming sounds and music, and to try to relax their muscles and general being. In the
neutral state, no stimulus
of music was provided. Finally, in the concentrated state, they ask the participants to follow a ball that was under one
cup, as that cup
was being shuffled among other 2 cups.

They made this experiments with 4 subjects, with each subject being tested twice on each mental state. For each
experiment, the MUSE headband
started recording after a while to be sure that the subject was in that mental state, and recorded for approximately 60
seconds, with a sampling rate
of an interval of 150-270 Hz. Since they applied a universal timestamp to each data point, it was possible to down
sampled the data into a sampling rate
of 250 Hz. With this procedure they ended up with 24 different trials (3 mental states x 4 subjects x 2 tries per mental
state), which translates to about
360,000 data points per channel (60 seconds x 250 Hz x 24 trials). For the total amount of data points taking in
consideration the 4 channels this amounts to
1,440,000 data points (350,000 x 4 channels), which is quite a good amount, and another reason why we chose to work on
this dataset and paper.

Before doing any feature extraction method, they down sampled the data to 150 Hz. After that they
rely on getting statistical features from the EEG data, FFT, max-min features in
temporal sequences, among others, in time windows to extract the best information
from the EEG data. The sliding window was set to 1s, and all the statistical features
are computed in this timeframe. Then some overlap for each next window was performed
at 0.5Hz.

<hr>
<h2>Preprocessing & Feature Extraction</h2>
<h4>1: Sliding window</h4>
<p>Windows run from [0s – 1s], [1.5s – 2.5s], [2s – 3s], [2.5s – 3s] continuing until the of the signals</p>
<p><b>Result:</b> N windows of signals</p>

![img.png](Pictures/sliding-window.png)
<h4>2: Calculate statistical 
</h4>
<hr>

<h2>Models</h2>

For the predicting models we focused on neural network models, Support Vector Machine (SVM), and
Random Forest Classifier.

<h3>Gated Recurrent Unit: GRU</h3>
<br>

<figure class="center">
  <img src="Pictures/GRU.PNG" alt="GRU" >
  <figcaption>Gated Recurrent Unit Model </figcaption>
</figure>
<br><br>

<p>Recurrent neural networks are great at "remembering" information and sequenced data,
so they are great for this brain-wave type of data. GRU is a simpler version of a Long-Short
Term Memory (LSTM), and since it's a simpler version, it is also a faster one.</p>

<h3>Support Vector Machine: SVM</h3>
<br>
<figure class="center">
  <img src="Pictures/SVM.PNG" alt="SVM" >
  <figcaption>Support Vector Machine </figcaption>
</figure>
<br><br>

<p>Support Vector Machines are also a good machine learning algorithms when it comes to research with brain waves.
This method helps in classifying by finding a hyperplane that separates the classes with the maximum margin between them.

For the experiments that we performed with SVM, we noticed that if we take too much data, SVM takes too much time to
perform. With this subset of data we can infer what would be the total result of the
#SVM algorithm if we had more computational power to work with.

<h3>Random Forest Classifier</h3>
<br>
<figure class="center">
  <img src="Pictures/RFClassifier.PNG" alt="RFC" >
  <figcaption>Random Forest Classifier </figcaption>
</figure>
<br><br>

<p>This method fits the data on a number of decision trees (n_estimators) on different sub-samples of the
data, taking the average of them all to improve the accuracy.</p>

<h3>Convolutional Neural Network: CNN</h3>
<br>
<figure class="center">
  <img src="Pictures/CNN.PNG" alt="CNN" >
  <figcaption>Convolutional Neural Network</figcaption>
</figure>
<br><br>
<p>
This last method is usually used for image classification. Those for image classification are usually.
for 3 dimensional data (using Conv2D). Nonetheless, 1-Dimensional Convolutional
Neural Networks are also used for time sequenced data, which is exactly what we got with these statistical
values and FFTs from each of the 4 channels selected.
</p>

<br><br>

<h2>Results</h2>

<p>For the Results section, we first analyze the results of the 4 models by performing these models
with only FFTs frequencies as the features that will be used as inputs in the model, and then we 
performed the analysis on both the FFTs and Statistical Features.</p>

<h3>Results with FFTs</h3>
<hr>
<p>The following tables present scores for Precision, Recall, and F1-Score metrics for each
type of model. These metrics and the accuracy graph presented below are a good indicator
of all good the model performs.</p>

<table>
<tr>
    <th><h3>GRU Results</h3></th>
    <th><h3>SVM Results</h3></th>
</tr>

<tr>
    <td>
        <figure class="center">
          <img src="Pictures/gru_results_ffts.PNG">
        </figure>
    </td>
    <td>
        <figure class="center">
          <img src="Pictures/svm_results_ffts.PNG">
        </figure>
    </td>
</tr>
<tr>
    <th><h3>RFC Results</h3></th>
    <th><h3>CNN Results</h3></th>
</tr>
<tr>
    <td>
        <figure class="center">
          <img src="Pictures/rfc_results_ffts.PNG">
        </figure>
    </td>
    <td>
        <figure class="center">
          <img src="Pictures/cnn_results_ffts.PNG">
        </figure>
    </td>
</tr>
</table>
<hr>
<p>This is the overall accuracies of the models when performing the predictions on only the FFTs features:</p>
<figure class="center">
  <img src="Pictures/accuracies_ffts.PNG">
</figure>

<h3>Results with Statistical Features + FFTs</h3>
<hr>

<table>
<tr>
    <th><h3>GRU Results</h3></th>
    <th><h3>SVM Results</h3></th>
</tr>

<tr>
    <td>
        <figure class="center">
          <img src="Pictures/gru_results.PNG">
        </figure>
    </td>
    <td>
        <figure class="center">
          <img src="Pictures/svm_results.PNG">
        </figure>
    </td>
</tr>
<tr>
    <th><h3>RFC Results</h3></th>
    <th><h3>CNN Results</h3></th>
</tr>
<tr>
    <td>
        <figure class="center">
          <img src="Pictures/rfc_results.PNG">
        </figure>
    </td>
    <td>
        <figure class="center">
          <img src="Pictures/cnn_results.PNG">
        </figure>
    </td>
</tr>
</table>
<hr>
<p>This is the overall accuracies of the models when performing the predictions on all the features (statistical features and FFTs):</p>
<figure class="center">
  <img src="Pictures/accuracies_allfeatures.PNG">
</figure>




<h2>EXTRA SECTION: SEED-IV Dataset </h2>

<h3>Seed IV Dataset</h3>

<p> Dataset Paper based on SEED-IV's dataset:</p>

<ul>
    <li>
    <a href= "https://bcmi.sjtu.edu.cn/~seed/seed-iv.html"> 
                DataSet: SEED-IV</a>
    </li>
    <li>
    <a href= "https://ieeexplore.ieee.org/abstract/document/8283814"> 
                Paper: EmotionMeter: A Multimodal Framework for Recognizing Human Emotions</a>
    </li>
    <li>
    <a href= "https://ieeexplore.ieee.org/document/7104132"> 
                Paper: Investigating Critical Frequency Bands andChannels for EEG-based Emotion Recognition with Deep Neural Networks</a>
    </li>
    <li>
    <a href= "https://pubmed.ncbi.nlm.nih.gov/28102833"> 
                Paper: A Multimodal Approach to Estimating Vigilance Using EEG and Forehead EOG</a>
    </li>
</ul>

<h4>Data Acquisition</h4>

The data collected from 15 participants watching 72 film clips that were maticulately chossen by a preliminary study.
These clips have the tendency to introduce happiness, sadness, fear or neutral emotions. The reearcher use 62-channel
ESI NueroScan Sytem and SMI eye-tracking glasses. For each subject, there are 3 sessions on different days. Each of the
sessions is 24 trials.

<h4>Feature Extraction</h4>

The signal is sliced into 4-second nonoverlapping segments

<h4>EEG Features</h4>

The raw EEG data have been downsampled to a 200 Hz sampling rate in order to remove the noise and the artifacts. Then
using bandpass filter betweeen 1 Hz - 5 Hz. By using power spectral density (PSD) and differential entropy (DE) to
eaxtract each segment at 5 frequency bands (delta, theta, alpha, beta, and gamma). The data also provide smoothing
technique between linear dynamic system (LDS) and moving averages

<ul>
    <li>
        Bandpass Filter
    </li>
    <li>
        Power Spectral Density
    </li>
    <li>
        Differential Entropy
    </li>
    <li>
        Linear Dynamic Sysstem
    </li>
    <li>
        Moving Averages
    </li>

</ul>

<h4>Eye Movement Features</h4>

Using various of parameters to extract namely: pupil diameter, dispersion, fixation duration, saccade, event statistics

<br><br>

<h4>Data Acquisition</h4>

The data collected from 15 participants watching 72 film clips that were maticulately chossen by a preliminary study.
These clips have the tendency to introduce happiness, sadness, fear or neutral emotions. The reearcher use 62-channel
ESI NueroScan Sytem and SMI eye-tracking glasses. For each subject, there are 3 sessions on different days. Each of the
sessions is 24 trials.

<h4>Feature Extraction</h4>

The signal is sliced into 4-second nonoverlapping segments

<h4>EEG Features</h4>

The raw EEG data have been downsampled to a 200 Hz sampling rate in order to remove the noise and the artifacts. Then
using bandpass filter betweeen 1 Hz - 5 Hz. By using power spectral density (PSD) and differential entropy (DE) to
eaxtract each segment at 5 frequency bands (delta, theta, alpha, beta, and gamma). The data also provide smoothing
technique between linear dynamic system (LDS) and moving averages

<ul>
    <li>
        Bandpass Filter
    </li>
    <li>
        Power Spectral Density
    </li>
    <li>
        Differential Entropy
    </li>
    <li>
        Linear Dynamic System
    </li>
    <li>
        Moving Averages
    </li>

</ul>

<h4>Eye Movement Features</h4>

Using various of parameters to extract namely: pupil diameter, dispersion, fixation duration, saccade, event statistics

<br><br>
















