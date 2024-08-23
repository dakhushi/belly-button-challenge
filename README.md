# belly-button-challenge
<img width="50%" src="https://github.com/dakhushi/belly-button-challenge/blob/main/images/microbes-sem.jpg">

## Summary of the assignment

This assignment is to build an interactive dashboard to explore the [Belly Button Biodiversity dataset](https://robdunnlab.com/projects/belly-button-biodiversity/) which catalogues the microbes that colonise human navels.
The dataset reveals that a small handful of microbial species (also called operational taxonomic units, or OTUs, in the study) were present in more than 70% of people, while the rest were relatively rare.

In this activity, I have created an interactive dashboard to visualize bacterial culture data from a JSON file using D3.js and Plotly. We implemented several key functionalities:

**Metadata Display:** Displayed metadata about the selected sample in a panel.

**Bubble Chart:** Created a bubble chart to represent the distribution of bacterial species in the selected sample.

**Bar Chart:** Built a bar chart to show the top 10 bacterial species found in the sample.

**Dynamic Interaction:** The dashboard allows users to select different samples from a dropdown menu, dynamically updating the charts and metadata display based on the selected sample.

The code uses D3.js for data manipulation and DOM updates, and Plotly for rendering interactive charts. 
This exercise provided hands-on experience with creating data visualizations and handling user interactions in a web-based dashboard.

**Step-by-Step Procedure followed to achieve the outcome**

**1. buildMetadata(sample) Function:**
This function is responsible for displaying the metadata (demographic information) for a given sample.

Detailed Steps:
- Fetch Data: The function uses d3.json() to load the dataset from the provided URL asynchronously.
- Filter Metadata: It filters the metadata array to find the object that matches the sample ID passed into the function.
- Select HTML Panel: The panel where the metadata will be displayed is selected using d3.select("#sample-metadata").
- Clear Panel: Any existing content inside the panel is cleared using panel.html("").
- Display Metadata: It loops over the key-value pairs in the filtered metadata object and appends them as "h6" elements to the panel. The key is converted to uppercase and displayed along with its corresponding value.

**2. buildCharts(sample) Function**
This function is responsible for building the bubble chart and bar chart based on the selected sample.

Detailed Steps:
- Fetch Data: The dataset is loaded using d3.json() just like in buildMetadata.
- Filter Samples: The samples array is filtered to find the object that matches the provided sample ID.
- Extract Data: The otu_ids, otu_labels, and sample_values for the selected sample are extracted.
- Bubble Chart Data:
    * The bubbleData object is created, which contains the x and y coordinates, marker size, and color information for the bubble chart.
    * x: OTU IDs.
    * y: Sample values (abundance of bacteria).
   * text: OTU labels for hover information.
   * marker: Determines the size and color of the bubbles.
   * Bubble Chart Layout: The layout for the bubble chart is defined with titles, margins, and axis labels.
   * Render Bubble Chart: The Plotly.newPlot() function is used to render the bubble chart on the HTML element with ID bubble.
     
     <img width="80%" src="https://github.com/dakhushi/belly-button-challenge/blob/main/images/bubble_chart.jpg">
     
- Bar Chart Data:
    * The bar chart displays the top 10 OTUs found in the sample.
    * yticks: The top 10 OTU IDs, mapped to strings and reversed to display the largest at the top.
    * x: Corresponding sample values.
    * text: OTU labels for the top 10 samples.
    * Render Bar Chart: The Plotly.newPlot() function is used to render the bar chart on the HTML element with ID bar.

 <img width="60%" src="https://github.com/dakhushi/belly-button-challenge/blob/main/images/barchart.jpg">
 
**3. init() Function**
This function initializes the dashboard when the page is first loaded.

Detailed Steps:
- Fetch Data: The dataset is loaded via d3.json() to retrieve the list of sample names.
- Select Dropdown: The dropdown menu with ID #selDataset is selected using d3.select().
- Populate Dropdown: The dropdown menu is populated with options for each sample in the dataset.
- Initialize First Sample: The first sample in the list is selected by default, and the charts and metadata panel are built for this sample by calling buildCharts() and buildMetadata().

<img width="30%" src="https://github.com/dakhushi/belly-button-challenge/blob/main/images/Demographic%20info.jpg">

**4. optionChanged(newSample) Function**
This function is triggered whenever a new sample is selected from the dropdown menu.

Detailed Steps:
- Update Charts and Metadata: This function calls buildCharts() and buildMetadata() with the newly selected sample ID whenever the dropdown menu selection changes. This ensures that the charts and metadata update to reflect the new sample.

**5. init() Call**
Finally, the init() function is called to initialize the dashboard when the page first loads.

[Belly Button Biodiversity Dashboard](file:///C:/Users/Kothari/Desktop/Satyen's%20Desktop/00%20Data%20Analitics%20Bootcamp-Khushi/Module%2014-Interactive-Visualisations/belly-button-challenge/index.html)
<img width="80%" src="https://github.com/dakhushi/belly-button-challenge/blob/main/images/dashboard%20.JPG">

### Resources:
- [Belly Button Biodiversity dataset](https://robdunnlab.com/projects/belly-button-biodiversity/)
- ChatGPT
- [Plotly Graphing Library](https://plot.ly/javascript/bubble-charts/)
- [D3 Documentation](https://d3js.org/d3-selection/selecting)
