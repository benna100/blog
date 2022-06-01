# How I hacked my sons Duplo train to go faster using my voice



So my son got a Duplo train for his birthday. The train is fairly advanced. There are different blocks you put on the tracks that make it do different actions: one will make the train turn on the light, one will reverse the driving direction of the train, one will make the train play a specific sound and one will make the train stop. 

On top of that you can control the train with an app (because of course). In the app you can control the speed, different sounds, the lights and the driving direction. The app connects to the train via Bluetooth and that gave me an idea 💡 

What if you could control the train using your voice ? Wouldn't that be cool!? 😎



## Research phase

Now I had to research if someone had tried something similar. That led me to a Dutch guy that had [put his sons duplo train on the blockchain](https://thenextweb.com/news/hacker-blockchain-train-duplo), where the train made sounds and drove around based on some events on his own alt coin.

The [script](https://gist.github.com/roelandp/e80ccc15bc5317e9704e2ac2b3573f42) for controlling the train was linked in his article, and the script led me to [node-poweredup](https://github.com/nathankellenicki/node-poweredup) - A Javascript module to interface with LEGO Powered Up components. Apparently LEGO has made lots of components that can be controlled via Bluetooth of which the Duplo train was one of them. 

✅ Was it possible to control the train - yes



## Connecting to the train

Now I knew it was possible to control the train, but could I make it work? 

My first stab at it was on my Windows machine. I went a bit too quick into it (story of my life) without checking the [prerequisites](https://github.com/abandonware/noble#windows). This gave me a lot of problems. When I finally found the prerequisites I saw that it was a lot easier using a Mac compared to Windows. 

So I booted up my work computer and quickly got a successful connection. Yeah 🥳 

The script that the Dutch guy had made was outdated though. The entire api had changed so into the [documentation](https://nathan.kellenicki.com/node-poweredup/) I dove 🏊‍♀️

It took a bit of time but I finally made the train drive and quickly learned to debug the train by putting it on its side. My arm was getting a bit tired after constantly moving the train back and forth (which is what you do to start and stop the train). 

✅ Could I control the train - yes



## Getting the pitch of someone's voice

On to the next problem: Figuring out if I could get the pitch of someone's voice. 

I knew this was possible. I had made a [previous project](https://github.com/benna100/clap-python-project) in python where clapping would start playing some music. This was done using a technique called [fft](https://en.wikipedia.org/wiki/Fast_Fourier_transform) where you transform the audio signal into its frequency domain.

But the connection to the train was made in nodejs. Therefore I had to do the pitch detection in nodejs. This proved to be a huge problem 🤔 I am still not really sure if it is possible. I tried out a few libraries but didn't really get anything working. 

Then I tried to approach it from another angle 🔎 What if I instead detected the pitch in the browser and then sent that detection to nodejs? Luckily there was a great library called [Pitchy](https://github.com/ianprime0509/pitchy) that solved this exact problem. Look at this simple, magnificent api with a [great, clear example](https://ianjohnson.dev/pitchy/) 👌

```const [pitch, clarity] = detector.findPitch(input, sampleRate);```

✅ Could I detect the pitch in someone's voice - yes



## Gluing everything together

All I had left from here was to glue everything together. That was done using [Socket.io](https://socket.io/). Socket.io lets you send data bidirectionally in real time. So from the client to the server and from the server to the client, simultaneously. 

Luckily I had also worked with that before while building an [online slime volley game](https://slime-volley-multiplayer.herokuapp.com/), so it did not take too long to get it working. The last tweaking was done around the [frequency of sending the data to the server](https://github.com/benna100/duplo-train-voice-control/blob/main/index.js#L37), how to [map the pitch to a train speed](https://github.com/benna100/duplo-train-voice-control/blob/main/index.js#L23) and [filtering the signal](https://github.com/benna100/duplo-train-voice-control/blob/main/index.js#L35) so that the train will only drive when someone is saying something.



## The final result 🚂

You can see the final result here: [I hacked my sons Duplo train 🚂💻](https://www.youtube.com/watch?v=t65X-cs55qM)

If you want to try it out for yourself, feel free; The code can be found [here](https://github.com/benna100/duplo-train-voice-control). Just remember the [prerequisites](https://github.com/abandonware/noble#prerequisites)!

Checkout [my portfolio](https://benna100.github.io/portfolio/) if you like these kinds of projects

