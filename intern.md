---
layout: default
title: Projects | 
---

# Intelligent Pump Control System

&nbsp;  
<img
    src = "/images/intern/IPCMachine.png"
    style = "width = 30%;
            height = 30%;"
    >
&nbsp;  

While I started working with my colleague on the IPC pump demo unit, I noticed the complexity of the system structure. It is well suitable for demonstrating the complete functions of the multi-pump system; there are various parameters can be adjusted to fit in different situations, however it takes a lot of time for a new user to know which should he adjust when operating. Take myself as example, I spend almost a month just to know all the controllable parameters and their effects. Since my major is human-computer interaction, I think it’s a good chance to apply everything I’ve learned to the project.  
&nbsp;  
The intention is to create a user-friendly interface for end users. The system is originally designed for engineers, so a new user have to pay some effort before giving the desired commands. Considering that the pump system might be exhibited to potential customers, even end users, it is necessary to build an easier version.  
&nbsp;  
This user-friendly version will be simple for the user to operate; with the knowledge that the ultimate goal of the multi-pump system is providing a stable output flow, the user can simply walk up to the control panel and enter the target flow. The system can immediately start to operate and be adjusted to the desired value within a short time interval, no additional controls are needed. Beside that, the system also provides live monitoring of working pumps and the output time chart for the user to quickly understand how the system is working at the moment.  
&nbsp;  
The multi-pump system comprises 4 pumps, 2 VFDs CP2000, and 1 HMI DOP-W127B. It is installed with a water tube, and tested inside the laboratory of Delta Electronics Eindhoven office.  
&nbsp;  

## Identifying Key Elements

When it comes to motor controls, there are a number of parameters that affects the performance, and the parameters that indicate how the motor is working. For controlling the most important one is RPM, which the abbreviation for “revolution per minute”; the higher the value is, the faster the motor is spinning, which then leads to larger flow. As for monitoring performance not only the RPM value is important, but also the actual flow within the pipes.  
&nbsp;  
Considering the tasks that will be assigned to the system, measuring the flow in the pipe is necessary. Thus the key parameters I identified are a) the RPM values of each motor, and b) the current output flow rate.  
&nbsp;  
Judging from the research, the parameters and controls I put in the menu bar are:  
> a) Operation status  
b) Motor working frequency  
c) Operation mode  
d) Set value  
e) Feedback value  
f) Run/stop button  
&nbsp;  

## The Refined Interface

<div
    class = "projectBox"
    >
    <table>
        <tr>
        <th
            style = "width: 50%;
                    height: 50%">
            <img
                src = "/images/intern/interface.png"
                alt = "The refined user interface(off)."
                style = "max-width: 95%;
                        max-height: 95%;
                        vertical-align: middle;"
                >
        </th>
        <th
            style = "width: 50%;
                    height: 50%">
            <img
                src = "/images/intern/running.png"
                alt = "The refined user interface(on)."
                style = "max-width: 95%;
                        max-height: 95%;
                        vertical-align: middle;"
                >
        </th>
        </tr>
    </table>
</div>  
&nbsp;  
&nbsp;  

## Acknowledgement  

Kevin Lu, Victor Ogedegbe, Ufuk Ozer, Vladimir Pana

## Company Website  

[Delta EMEA](http://www.delta-emea.com)  
