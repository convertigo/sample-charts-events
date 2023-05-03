
# ![](https://github.com/convertigo/convertigo/blob/develop/engine/src/com/twinsoft/convertigo/beans/core/images/project_color_16x16.png?raw=true "Project") sample_charts

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





<details><summary><span style="color:DarkGoldenRod"><i>Connectors</i></span></summary><blockquote><p>


## ![](https://github.com/convertigo/convertigo/blob/develop/engine/src/com/twinsoft/convertigo/beans/connectors/images/sqlconnector_color_16x16.png?raw=true "SqlConnector") void

void connector, replace or don't use it

<details><summary><span style="color:DarkGoldenRod"><i>Transactions</i></span></summary><blockquote><p>


### ![](https://github.com/convertigo/convertigo/blob/develop/engine/src/com/twinsoft/convertigo/beans/transactions/images/sqltransaction_color_16x16.png?raw=true "SqlTransaction") void

does nothing
</p></blockquote></details>
</p></blockquote></details>

<details><summary><span style="color:DarkGoldenRod"><i>Mobile Application</i></span></summary><blockquote><p>


## ![](https://github.com/convertigo/convertigo/blob/develop/engine/src/com/twinsoft/convertigo/beans/core/images/mobileapplication_color_16x16.png?raw=true "MobileApplication") Application

Describes the mobile application global properties

<details><summary><span style="color:DarkGoldenRod"><i>Pages</i></span></summary><blockquote><p>


### ![](https://github.com/convertigo/convertigo/blob/develop/engine/src/com/twinsoft/convertigo/beans/ngx/components/images/pagecomponent_color_16x16.png?raw=true "PageComponent") Page

My First Page as root page
</p></blockquote></details>
</p></blockquote></details>
