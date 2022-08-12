# MaxGrooVAE


This repository contains a GrooVAE Max implementation, which is designed to take beat-emphasis information from the user,
and return a "human-like" drum pattern that can be played and altered in real-time. The drum patterns will generally have a great deal
of dynamics (variable velocity) and groove (non-quantized beats).

The Max device has 4 'banks' for storing rhythms; this means that playback in Ableton can continue
uninterrupted whilst the python script develops new rhythms in the background. The user can instantly switch
between each of the 4 stored rhythms, allowing them to quickly preview different drum patterns.

There is further control given to decrease density (randomly drop out notes, with differential weighting according
to the type of drum) as well as the range and bias of output velocities. These controls are applied at the final stage of processing,
meaning that they can be tuned in real-time with no added latency.

It works only with 4-4 time signature for 2 bars with 1/16th note steps. The system can work in real-time in the sense that the composition of the next 2 bars would be completed before 2 bars worth of time until about 150 BPMs.

## Installation

1) Install magenta: https://github.com/magenta/magenta
(In our experience, this does not work on python versions above 3.7)

2) Activate the virtual environments and run the python code using

python MaxGrooVAE.py --send-ip=<Max IP> --send-port=<Max Port> --receive-ip=<Local IP> --receive-port=<Local port>
(alternatively, run the program in an IDE where you will be prompted for the ports)

3) Open the Max patch within Ableton and enter the corresponding ports/IP's

4) Input rhythms in the GrooVAE sequencer, specify temperature and which groove banks to overwrite, and hit 'fire'

5) If the OSC connection is succesful, it will 'de-active' the selected groove banks

6) Hit play in Ableton, and select which groove you want to hear (along with associated playback values)



## Limitations

We acknowledge that it is difficult for musicians to run a python script whilst creating. Our top priority would
be to incorporate the model into a Javascript application natively within Max. If you are interested in
helping us to implement this, please reach out!

Furthermore, due to the limitations of the Magentaa GrooVAE model, we can only send/receive 2-bar compositions in 4/4 time signature.
It would be our desire in future work to see greater flexibility in length, as well as a broader scope of genres anad time signatures.


## Acknowledgements

This project is built around the GrooVAE model creataed by the Magenta team at Google:

https://magenta.tensorflow.org/

https://magenta.tensorflow.org/groovae

This was initially creataed as a final project for the Pompeu Fabra Universty - Computational Creativity Class Project
in March 2022.

Julian Lenz: julianlenz981@gmail.com
Recep Oğuz Araz: oguza97@gmail.com
