# The Need of the Hour - an Accessibility Device for AI-based Lip Reading
-	The hearing impaired have a tough time communicating, because hearing aids can't isolate voices from crowds
-	Most good hearing aids are beyond the means of the communities of people that need them, with pricetags upwards of 3000$
-	Sign Language is a viable alternative for communication but it is limited in applicability
-	Following the lockdown restrictions, most means of education and communication have moved online over Zoom, Discord and Skype. While this has been a minor inconvenience to most of us, the impacts on the hearing impaired community have been nothing short of catastrophic. Online lectures are a whole new challenge with audio and video buffering, subtitles not an option and a fast paced classroom environment.  

# Overview of our Project - Introducing Lip Sync!
LipSync is an application that performs lip reading using a combination of supervised learning and Natural language Processing (NLP). It can supplement hearing aids in lectures by ignoring background noise (by lipreading and transcribing spoken content), and enable audio independent communication where speech recognition falls short. Lip Sync's ability to transpose movement into text could be made nearly instant, and help students remain engaged instead of catching up to traditional methods of transposing speech which come with the punishment of long wait times for information.

## Algorithm and Workflow - 4 steps
### 1. Accepting video input
The application accepts video in .mpg format. .avi and .mp4 files need to be converted into .mpg for use with the LipNet packages 
### 2. Using LipNet
Using spatiotemporal convolutional neural networks, it encodes the changes in visual information over time to map sequences of lip movements to words. It then uses bi-directional gated recurrent units to determine how much information to persevere and forget, so that the starting and ending of words can be demarcated. Multilayer perceptrons then aggregate all of this information together to finally output a transcription of spoken content. This transcription can then be converted into audio, or even into braille (for those who are visually impaired as well).
### 3. Passing LipNet output through a WordBag
A WordBag is an NLP method of identifying the likeliness of a certain word being used in conversation given the other words in the bag. In this case, the plasce the words hold in the sentence doesn't matter as much as the frequency of the word. Passing the LipNet text output through a WordBag improves accuracy of text output since context is taken into account in a probabilistic sense
### 4. Releasing video output with text
The final output is a video with text added onto it. Current applications of LipNet boast upto a 93% accuracy, 14% higher than the average text to speech software available today. We believe that This prototype could average a surprisingly high word accuracy of between 60 and 80% that could stretch even to 95%.

## Usage
Lip Sync has a simple 3-stage workflow: 
1. Using a RaspberryPi, Helen records video of speaker. 
2. It then transmits this video information to a system running LipNet - the AI that performs lip reading 
3. LipNet analyses the video and outputs a transcription of what was spoken during the video. 

## A Summary of Technology Used and Our Design Process
### Keras, TensorFlow Framework
### LipNet Neural Network
This model uses the GRID corpus (http://spandh.dcs.shef.ac.uk/gridcorpus/) as a dataset for training LipNet. LipNet is a convolutional Neural Network that identifies lip movements in frames and is capable of translating this into characters and words based on phonemes. It was theorized by Yannis et al at Oxford University. The implementation that we chose to use consisted of a series of python packages executed in Keras and made available open source.  
### Python NLTK
### CUDA
### aws
```
print('Listening')
s3 = boto3.client('s3')
bucket_name = 'helen-v1bf79919b2e794658b84abfe4dde08f44pkhelenenv-pkhelenenv'
file_names = []
```
## Potential Future Applications
- With enough datasets and time, Lip Sync's ability to transpose movement into text could be made nearly instant, and help students remain engaged instead of catching up to traditional methods of transposing speech which come with the punishment of long wait times for information.
- Lip Sync could potentially develop into a real time transcribing phone app for ios and android improving accessibility for the hearing impaired everywhere
- LipReading software could potentially be used for forensic purposes and for identifying speech in videos through loud noises
- Lip Sync could additionally be used to create and maintain repositories of speeches and poetry obtained from fragile videotapes.  

### Citations
1. 'LipNet: End-to-End Sentence-level Lipreading' by Yannis M. Assael, Brendan Shillingford, Shimon Whiteson, and Nando de Freitas (https://arxiv.org/abs/1611.01599).
2. James Dyson Award - Helen (https://www.jamesdysonaward.org/en-HK/2019/project/helen/)
3. Implementing Lipnet through Keras (https://github.com/rizkiarm/LipNet)
4. Text Summarization (https://github.com/urandom/text-summary)
