


# sample_charts

A Sample to show how Charts can be interactive. User can click on a Chart element and this will generate an Event that can be caught in the page. The app is free to use this event to display a message (Shown in the sample) or to call a Back end Sequence to process data according to the event ..

## How does this work ? 
The magic  comes from the Chart configuration see the _Chart Options_ property and set it to :

<pre>
	{'plugins':{'title':{'display': true,'text': 'My Chart Title'}, 'responsive': true, 'maintainAspectRatio': false}, onClick: this.chartOnClick.bind(this) }
</pre>

Note the _onClick: onClick: this.chartOnClick.bind(this)_

This will call a function each time an element is clicked on the chart. You just have to implement this function in your page class :

* Right Click on Page -> Edit Page Class
* In the page class code at the end find the  	/*Begin_c8o_PageFunction*/ /*End_c8o_PageFunction*/ section
* Between the BeginXXX and End XXX write this code :
<pre>
	/*Begin_c8o_PageFunction*/
	chartOnClick(event, clickedElements, chart) {
		const { dataIndex, raw } = clickedElements[0].element.$context
  		const barLabel = event.chart.data.labels[dataIndex]
  		this.label = barLabel;
  		this.dataValue = raw;
  		
		this.getInstance(Events).publish('chartClicked', { label: barLabel, value: raw});
	}
	/*End_c8o_PageFunction*/
</pre>






For more technical informations : [documentation](./project.md)

- [Installation](#installation)
- [Mobile Application](#mobile-application)
    - [Pages](#pages)
        - [Page](#page)


## Installation

1. In your Convertigo Studio click on ![](https://github.com/convertigo/convertigo/blob/develop/eclipse-plugin-studio/icons/studio/project_import.gif?raw=true "Import a project in treeview") to import a project in the treeview
2. In the import wizard

   ![](https://github.com/convertigo/convertigo/blob/develop/eclipse-plugin-studio/tomcat/webapps/convertigo/templates/ftl/project_import_wzd.png?raw=true "Import Project")
   
   paste the text below into the `Project remote URL` field:
   <table>
     <tr><td>Usage</td><td>Click the copy button at the end of the line</td></tr>
     <tr><td>To contribute</td><td>

     ```
     sample_charts=https://github.com/convertigo/sample-charts-events.git:branch=main
     ```
     </td></tr>
     <tr><td>To simply use</td><td>

     ```
     sample_charts=https://github.com/convertigo/sample-charts-events/archive/main.zip
     ```
     </td></tr>
    </table>
3. Click the `Finish` button. This will automatically import the __sample_charts__ project


## Mobile Application

Describes the mobile application global properties

### Pages

#### Page

My First Page as root page



