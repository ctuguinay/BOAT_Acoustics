(acoustics-intro)=
# Conceptual framework

In this tutorial, we will develop a solid understanding of how to breakdown an ocean acoustics problem into distinct components that can each be analyzed separately. This "systems" approach provides a structured framework that will help us gain a holistic picture of the problem.




## Learning goals

Taking a systems approach to understanding ocean acoustics problems, our learning goals are to be able to:
1. Identify key components of the **system** underlying the problem
2. Analyze the relationships of different components within the system
3. Differentiate known and unknown components
4. Assess what can be realistically achieved when characterizing the unknowns
5. Recognize potential caveats in the measurement, inference, or estimation processes




(acoustics-intro_motivation)=
## Motivating example: The acoustic lives of the orcas

<!-- Description of scenarios without using the sonar equation first -->

Let's start with a general overview of ocean acoustics problems with a motivating example.
For both fun and to highlight the interdisciplinary nature of ocean acoustics, we will use the lives of orcas, or or killer whales (_Orcinus orca_), to guide our exploration.
Through this example, you will see how the physics of sound, the biology of whales and fish, the ocean environments, and scientific instruments all play a role in this problem.


### How and when do orcas use sound?
Killer whales are toothed whales (odontocetes) that use sound to communicate with each other and find food in the ocean. There are two types of killer whales living on the west coast of the north American continent: the ["resident" and the "transient"](REF) killer whales.

Resident killer whales typically hang out in coastal waters and primary feed on fish, such as salmon. Since many fish don't make sound, whales produce impulsive and directional sounds (the ["clicks"](REF)) and use the returning echoes to find, track, and catch the fish. This is a special sensing modality called "echolocation," which is also used by all toothed whales and most bats. 

<!-- In this case, these fish species don't hear sounds produced by the killer whales because that is beyond their hearing range. However, note that this is not always true, as there are fish species with specialized high frequency hearing capability that can hear sounds above 20 kHz (which is considered "ultrasonic" for humans). -->

Transient killer whales, on the other hand, rely on both listening and echolocation to hunt marine mammals, such as seals. Since seals use sound to communicate and hear well underwater, transient killer whales eavesdrop on seal vocalizations to detect and localize them, then switch to intensive echolocation clicks during active pursuits.

Both resident and transient killer whales use a rich repertoire of sounds to communicate. Research has shown that killer whales in matrilineal groups centered around related females (the "pods") have [distinct call patterns](https://orca.research.sfu.ca/call-library). This allows us to acoustically infer their group identity, which is really useful in studying these fully aquatic mammals.

### How do we use ocean acoustics techniques to study orca?
Given killer whales' extensive use of sound in communication and foraging, we can leverage hydrophones to detect their presence, identify the groups, and infer their activities (e.g., feeding or socializing). As each hydrophone has a limited effective listening range, we can use a network of hydropohones to monitor whales over a larger special area. This is precisely what [Orcasound](https://www.orcasound.net/) is doing in the northeast Pacific Ocean. 

EMBED SPECTROGRAM EXAMPLE WITH SOUND
LINK TO SPECTRAL ANALYSIS PAGE
<!-- One can also use multiple closely spaced hydrophones to accurately localize the whales. -->

Scientists attach small electronic "tags" equipped with hydrophones and other sensors to whales. These tags record the sounds whales produce and hear, alongside their movements, offering a perspective from the whale's point of view. For example, an [echogram](REF) like below visually depicts what the whale may be hearing in the echoes when closing in on a prey item.

ADD CLICK ECHOGRAM

Knowing all the above, we can start to ask questions like:
- How far can killer whales hear each other? How far can we detect them using hydrophones? Does this distance change depending on the type of sound whales emit?
- How do whales identify different fish species through echolocation? How do echoes change with fish size or when there are multiple fish?
- What makes a good hydrophone to detect the whales? What key characteristics should we consider?

Below, we will introduce the mighty "SONAR equation" to help us answer these questions.


<!-- 
- other examples
    - blue whales communicate across ocean basin
    - humpback whales cultural transmission of call units
 -->




(acoustics-intro_sonar_equation)=
## The mighty SONAR equation

The Sonar Equation provides a framework for understanding the different components involved in either **pure listening** or **active pinging (echolocation)** using sound. The term **SONAR** stands for **SO**und **N**avigation **A**nd **R**anging.

In pure listening scenarios, the sonar equation is written as:

(acoustics-intro_sonar_equation_passive)=
$$
\textrm{RL} = \textrm{SL} - \textrm{TL},
$$

and in the active sensing scenario, it is written as:

(acoustics-intro_sonar_equation_active)=
$$
\textrm{RL} = \textrm{SL} - 2\textrm{TL} + \textrm{TS}
$$

where:
- $\textrm{RL}$ denotes receive level, or the strength of the received sound
- $\textrm{SL}$ denotes source level, or the intensity of the emitted sound
- $\textrm{TL}$ denotes transmission loss, or the attenuation of sound as it travels
- $\textrm{TS}$ denotes target strength, or the acoustic reflectivity of the target

You may find variations of the sonar equation that include additional terms, such as noise level ($\textrm{NL}$), array gain ($\textrm{AG}$), or directivity index ($\textrm{DI}$), as seen on the [DOSITS](https://dosits.org/science/advanced-topics/sonar-equation/) website. These variations arise from the specific problem setup and the instrumentation used.


```{Note}
:class: note
The SONAR equation effectively breaks down the complex ocean acoustics "system" into multiple individual pieces that are each much more manageable, making it a lot easier to analyze and model first each component and ultimately the whole system.
```


In the following tutorials, we will use the SONAR equation as a guide to explore key components of an ocean acoustics problem (the "system"), including acoustic sources and receiver (both biological or human-made), sound propagation and scattering (due to biotic or abiotic factors), and applications of signal processing and statistical methods to real-world ocean acoustic data through both conceptual introductions and hands-on exercises.

But first, let's see how we can use the SONAR equation to help us break down the complex problem of studying the lives of orcas using sound.

```{Tip}
:class: tip
Through the tutorials, you will find that each term in the SONAR equation is much more than just a level (intensity) that you see here, but that the SONAR equation remains a useful tool to think about the big picture when you work on an ocean acoustics problem.
```




(acoustics-intro_orca_and_sonar_equation)=
## The lives of orcas through the SONAR equation
<!-- 
- How far can killer whales hear each other? How far can we detect them using hydrophones? Does this distance change depending on the type of sound whales emit?
- How do whales identify different fish species through echolocation? How do echoes change with fish size or when there are multiple fish?
- What makes a good hydrophone to detect the whales? What key characteristics should we consider?
-->

We first consider the scenario of Oli trying to communicate with Ola, and examine how different terms in the SONAR equation come into play:

(acoustics-intro_orca_comms)=
```{image} ../images/0_intro/orca_comms.jpg
:width: 600px
:align: center
```

You can see here that $\textrm{SL}$ characterizes how loud Oli is calling, $\textrm{TL}$ describes how much sound energy is "lost" before the sound reaches Ola, and $\textrm{RL}$ represents how loud the sound is when Ola receives. Depending on what the environment Oli and Ola are in, the content of Oli's signal (e.g., spectrum), Ola may or may not be able to hear Oli, or hear clearly what Oli is saying.

For example, if they are in a shallow channel, Oli's sound may bounce around between the sea surface and seafloor ("multipath" propagation) and cause Ola to hear multiple copies of the same sound. It also turns out that Oli's sound may not reach as far in warmer water compared to in colder water. You will learn more about these in the following sections.

<!-- One can imagine that the ambient noise can affect this too. -->

What if we want to predict how far we can detect Oli? It's pretty straightforward: just replace Ola with a hydrophone:

```{image} ../images/0_intro/orca_hydrophone.jpg
:width: 600px
:align: center
```

But of course, we need to consider if Ola and the hydrophone receives sound the same way, just like different people may hear the same sound differently.

Now let's consider the scenario where Ola wants to detect and track down a fish. The picture then changes to the following:

(acoustics-intro_orca_fish_echo)=
```{image} ../images/0_intro/orca_fish_echo.jpg
:width: 600px
:align: center
```

In this case, instead of Oli making a sound, now we have Ola's echolocation signal bouncing off the fish, characterized by $\textrm{TS}$. Because the sound now travels both from Ola to the fish, and from the fish to Ola, the amount of sound energy loss doubles, represented by $\textrm{2TL}$. Similarly, depending on the environment Ola is in and the type and number of fish there are, the exact situation may be more complex then what is depicted here. You will also learn more about these in the following sections.





(acoustics-intro_widgets)=
### Widget exercise

Let's put what we just learn to use! Below is an interactive "widget" that you can use to get an intuitive sense of how loud Oli's sound or fish echoes Ola may receive.

```{Tip}
:class: tip
Throughout the tutorials, we will use widgets to help develop physical intuitions behind ocean acoustics problems.
```

Here, all the numbers are represented in **decibels**, or "**dB**," which is a unitless, logarithmic measure widely used in ocean acoustics. We use the this measure in order to easily compare sound as loud as a jet taking off right outside of your window (~140 dB re 20 $\mu$Pa) with sound as soft as dropping a needle on the floor (~15 dB re 20 $\mu$Pa). Go to the [](primer-decibel) page to learn about this useful measure.

ADD_WIDGET:
- PASSIVE: RETURN RL FROM TL AND SL SLIDEBARS
- ACTIVE: RETURN RL FROM TL, SL, AND TS SLIDEBARS

**Try this for yourself:** By keeping $\textrm{TL}$ the same, you can see how much harder it is to hear fish echoes compared to Ola's sound, just because the sound needs to travel twice of the distance! Note that $\textrm{TL}$ is also typically a negative number when measured in decibel, which we will explain in [](acoustics-target_strength).





(acoustics-intro_exercises)=
## Apply the SONAR equation to other ocean acoustics problems

Having seen how the SONAR equation can be applied to study the orcas, let's try to apply the same principle to analyze another couple ocean acoustics problems.

### Exercise 1: "Looking" under the sea surface using an echosounder
Echosounder are high-frequency sonar systems widely used to "image" the interior of the ocean. It operates by transmitting signals ("pings") and receiving echo returns from any objects or boundaries underwater. Below is a sketch of how an echosounder measurement scenario looks like:

ADD PICTURE

Try to see if you can figure out the following:
- Identify the various terms in the SONAR equations in this sketch
- Identify at least one scientific question or application that can benefit from using an echosounder

### Exercise 2: Apply to your own research
If you have done or are thinking about doing research on an ocean acoustics-related topic, what is it? Think of one question you may want to answer or an application you may want to try, and try to see if you can figure out the following:
- Put together a quick sketch of the "system" of your ocean acoustics problem
- Identify the various terms in the SONAR equations in this sketch
- Identify at least one component in the sketch or one term in the SONAR equation that you would like to learn more about from the tutorials
<!-- - Submit your question [here](LINK): we will periodically answer these on the Ocean Acoustics & Technology forum! -->




(acoustics-intro_others)=
## How are these related to our daily lives?

Outside of ocean acoustics, how are the elements introduced above relate to our daily lives?

As humans, sound play an important role in how we perceive the world. For example: We can usually tell how heavy the rain is by the sound of raindrops hitting the windows. In a large and empty room, we "hear" the space through echoes of our own voices. Attending a concert or singing in a group can be a deeply emotional experience. Many unsighted people also use sound to navigate, including developing the capability to [echolocate](REF)! 

On a smaller scale and with higher resolution, we apply similar principles in medical ultrasound, a non-invasive diagnostic tool that uses sound waves to image the human body.

In addition, **radar** (**RA**dio **D**etection **A**nd **R**anging) also operates on the same principles, but uses electromagnetic waves instead of sound for sensing. It is widely used to track airplanes, characterize weather phenomena (e.g., cloud, rain, snow), and even observe the migration of large bird groups in the night sky. 

The principles we explore in these tutorials are not just relevant to ocean acoustics: They can also help us understand how we experience sound in our environment and how similar technologies shape our world.
