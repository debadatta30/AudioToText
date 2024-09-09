# AudioToText
This code converts an audio file to text transcript using a serveless architectutre which use the flow , An audio file uploadee to Amazon S3 which invokes an event to trigger a AWS Lambda which uses Amazon Transcribe to conver the audio file to text transcript.You can use this to capture the meeting details in transcipt and later use for analysis. The Architecture diagram shown below:
![image](https://github.com/user-attachments/assets/eb7057dc-656c-4df0-b8e5-3c6d01c45c47)


