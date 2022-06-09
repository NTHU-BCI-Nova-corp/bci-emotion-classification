[//]: # (Styles:)

<style>
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 70%;
}
</style>


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
<p> SEED-IV Dataset Paper based on this dataset:</p>
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

<h3>Seed IV Dataset</h3>

<br><br><br><br><br><br><br>

<h2>Preprocessing</h2>

<br><br><br><br><br><br><br>

<h2>Feature Extraction</h2>

<h3>Models</h3>


<br>

<h2>Results</h2>


