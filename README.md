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
</ul>


<h2>Dataset</h2>

<h3>Jordan-Bird et. al Dataset</h3>

In Jordan J. Bird's research, he and his team based themselves on trying to classify mental activity into relaxing,
neutral, and concentrating states.
They used the commercially available Muse headband, to focus on 4 EEG Sensors: (TP9, AF7, AF8, and TP10). Theses 4
channels were selected because past research
states that they are the good indicators of this mental activity, and also because of the easier availability for the
general public to get hold of one of these
devices. They have gathered the data and method from several experiments, but the latest one is from "Mental Emotional
Sentiment Classification with an EEG-based Brain-machine Interface":


<figure class="center">
  <img src="Pictures/4_channels_used.png" alt="Channels used" >
  <figcaption>Fig.1 - EEG sensors TP9, AF7, AF8 and TP10 of the Muse headband</figcaption>
</figure>
<br>

The data was collected from 2 individuals, one male and one female. They watched 6 films
for 60 seconds each, for each of the 3 different mental states, producing 18 minutes of data
for each individual. This results in 36 minutes of EEG in total (18 minutes x 2). The resulting
dataset results in 324,000 points (36 minutes x 60 seconds/minute x 150 Hz/second). The following 
movies and their

Before doing any feature extraction method, they down sampled the data to 150 Hz. After that they
rely on getting statistical features from the EEG data, FFT, max-min features in
temporal sequences, among others, in time windows to extract the best information
from the EEG data. The sliding window was set to 1s, and all the statistical features
are computed in this timeframe. Then some overlap for each next window was performed
at 0.5Hz.

<h4>Features Used:</h4>

<ul>
    <li>
        Statistical Features:
    </li>
    <li>
        Max, Min, Derivatives:
    </li>
    <li>
        Frequency Domain:
    </li>
    <li>
        Frequency Domain:
    </li>

</ul>

<br>

<h3>Seed IV Dataset</h3>

<h4>Data Acquisition</h4>

The data collected from 15 participants watching 72 film clips that were maticulately chossen by a preliminary study. These clips have the tendency to introduce happiness, sadness, fear or neutral emotions. The reearcher use 62-channel ESI NueroScan Sytem and SMI eye-tracking glasses. For each subject, there are 3 sessions on different days. Each of the sessions is 24 trials.



<br><br><br><br><br><br><br>

<h2>Preprocessing</h2>

<br><br><br><br><br><br><br>

<h2>Feature Extraction</h2>

<h3>Models</h3>


<br>

<h2>Results</h2>


