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
&nbsp;  

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

### Major Contribution 2: Implement Required Functions with nvd3  

Using the library nvd3 I implemented functions of *a) zoom in along x axis* and *b) panning* with the test data for further analysis of candidate libraries.  
&nbsp;  

### Major Contribution 3: Implement WebSocket API for the Team  

Upon deciding the connection method, one of the candidates is the WebSocket connection. I implemented the method and created an easy-use API for the team to incorporate with their code. Below is the code snippet.  

<div style = "background-color: rgb(50, 50, 50);"><pre><code class = "language-css">
class connection {
  constructor(url, actionOnReceiving) {
    // Set up connection
    try {
      this.ws = new WebSocket(url);
      setSocketBehavior(this.ws, actionOnReceiving);
    } catch (exception) {
      console.error(exception);
    }
  }
 
  // Send request to server
  sendRequest(req) {
    waitForSocketConnection(this.ws, () => {
      console.log("Send request: " + req);
      this.ws.send(req);
    });
  }
}
 
function setSocketBehavior(ws, actionOnReceiving) {
  // Set behavior on opening socket
  ws.onopen = () => {
    console.log("Start connection");
  };
 
  // Set behavior on closing socket
  ws.onclose = () => {
    console.log("Close connection");
  };
 
  // Set behavior on error
  ws.onerror = (error) => {
    console.error(error.msg);
  };
 
  // Set behavior on receiving message
  ws.onmessage = (receivedData) => {
    actionOnReceiving(receivedData);
  };
}
 
// Call callback until the connection is made
function waitForSocketConnection(socket, callback) {
  setTimeout(() => {
    try {
      if (socket.readyState == WebSocket.OPEN) {
        if (callback != null) {
          callback();
        }
      } else {
        console.log("Waiting for connection...");
        waitForSocketConnection(socket, callback);
      }
    } catch (error) {
      console.error(error);
    }
  }, 50); // wait 5 millisecond for the connection...
}
 
export default connection;
</code></pre></div>
&nbsp;  

### Major Contribution 4: Integrating and Refactoring Code

Upon delivering the result to the whole team, I participated in integrating the codes from my colleagues in the front end team. The major contribution was modularizing the functions and packaging them into different files.  
&nbsp;  

### Additional Contributions

a) Fulfilled responsibility by completing all user stories assigned  
b) First integration with the back end team  
c) Provide some suggestions to the back end team in regard of making and sending remarks on the data  
&nbsp;  

## The Interface

<img
    src = "/images/onera/interface.png"
    alt = "The screenshot of CloViTo."
    style = "max-width: 95%;
            max-height: 95%;
            vertical-align: middle;"
    >  
&nbsp;  

## Acknowledgement  

Janice Conquet, Niki Saleki, Dan Chirascu, Lkham Nyambuu, Hasan Kaplan, Christian Degott, Sedihgeh Arasteh, Abolfazl Saravani, Akash Arora, Respa Putra, Lamisha Rawshan, Ankith Bale, Shubham Rawal, Nastaran Bajalan, William Jawad, Mohammad Ibrahim

## Related Links  

[Onera Health](https://www.onerahealth.com)  
