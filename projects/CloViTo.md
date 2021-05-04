---
layout: default
title: Projects | 
---

# Cloud-Native Sleep Data Visualization Tool

The project “Cloud Native Sleep Data Visualization Tool” is a training project involving the Software Technology PDEng Program of TU/e and Onera Health. The project’s goal is to develop a visualization tool for medical workers to examine the EEG signals recorded when the patients were sleeping; this tool will play a significant role in assisting analyzing  the analysis of the sleeping patterns by simplifying the EEG signals, and convert the signals into readable forms.  
&nbsp;  
Within the project I played the rols as **Engineer/ Designer** in the frontend team. The team was responsible for designing and implementing all the following features:  
> a) Be able to receive raw data from local devices/end users  
b) Be able to extract and convert raw data into plottable files  
c) Be able to display a chart the user can interact with by allowing the user  
>> i) to zoom in/out  
ii) to scroll horizontally/vertically through the chart(panning)  
iii) to make marks/annotations

## Personal Contributions

I was majorly involved in the research stage and the final integration. To figure out the most suitable programming language and library, I conveyed tests on one of our candidates and implemented few functions derived from the feature requirements. Finally, I integrated code from other team members into the first verion of our deliverable.
&nbsp;  

### Major Contribution 1: Functionality Test for JavaScript Library *nvd3*

To decide which library suits our visualization needs the best, the team conveyed a series of research of all candidate libraries. I was assigned to the nvd3 library and completed a set of tests. The result obtained is put in the table below.  
&nbsp;  
| Functionality | Result |
|-|-|
| Support for Zoom | Yes |
| Max number of points | 100K is possible |
| Chart Type | No 3d chart |
| Accessibility | Yes |
| Support for Panning | Yes |
| Support for Tooltip | Yes |
| License | Apache 2.0 (Free) |
| Performance - init time of chart | 7ms |
| Performance - draw time of chart (ms) | 320 |
| Performance - span 5 sec (ms) | 840 |
| Performance - zoom 30s - 10s (ms) | 139 |
| Summed performance (ms) | 1299 |
| Support for range annotations / highlighting time range | Supports specific model (lineWithFocusChart) |
| Multiple Y values per X | Yes |
| Support for synchronisation | - |  
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
