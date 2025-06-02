This guide provides a comprehensive overview of using Dataflows Gen2 in Microsoft Fabric for visual data ingestion and transformation. It's designed for quick reference and as a study material, focusing on the capabilities and practical steps involved.

### 1\. Introduction to Dataflows Gen2 in Microsoft Fabric

**Dataflows Gen2** in Microsoft Fabric (part of the Data Factory experience) offer a powerful, low-code/no-code approach to data ingestion and transformation. They leverage the familiar **Power Query Online** experience, allowing users to visually connect to various data sources, apply complex transformations, and load the prepared data into a Lakehouse, Data Warehouse, or other Fabric destinations.

**Key Purpose and Benefits:**

  * **Visual Data Preparation:** Empowers business users and data engineers to clean, transform, and reshape data without writing code.
  * **Multi-Step Data Ingestion:** Supports complex ingestion scenarios with multiple transformation steps.
  * **Integration with Power Query:** Utilizes the robust and widely adopted Power Query engine.
  * **Seamless Fabric Integration:** Dataflows Gen2 are native Fabric items, easily integrated with other Fabric workloads like Data Pipelines.
  * **Scalability:** Leverages Spark compute in the background for scalable data processing.

### 2\. Understanding Dataflows Gen2 Capabilities

  * **Power Query Online Editor:** The core interface for building data transformation logic. It's the same robust experience found in Power BI, allowing for a wide range of transformations.
  * **Over 150 Data Connectors:** Connect to a vast array of data sources, including databases (SQL Server, Azure SQL, PostgreSQL, MySQL), cloud storage (Azure Data Lake Storage Gen2, Azure Blob Storage), SaaS applications (Salesforce, SharePoint), web APIs, and more.
  * **Staging Data:** Dataflows Gen2 automatically stage data to your Fabric Lakehouse, providing an intermediate storage layer that improves performance and reliability, especially for large datasets. This also helps with reusability.
  * **Output to Fabric Destinations:** Directly output transformed data into a Lakehouse (as Delta tables) or a Data Warehouse, making it immediately available for further analytics, reporting, or machine learning.
  * **Schema View:** Allows you to define or modify the output schema of your dataflow, ensuring data consistency and correctness.
  * **Next-Gen Compute Engine:** Utilizes optimized compute for faster performance and lower resource consumption compared to older Dataflows.

### 3\. Creating Dataflow Gen2 Solutions to Ingest and Transform Data

The process of creating a Dataflow Gen2 typically involves three main phases: Get Data, Transform Data, and Set Data Destination.

#### a. Phase 1: Get Data (Connecting to a Data Source)

1.  **Create a New Dataflow Gen2:**
      * In your Microsoft Fabric workspace, select "New" \> "Dataflow Gen2" under the "Data Factory" section.
2.  **Choose a Data Source:**
      * The Power Query Online editor will launch, presenting a wide range of connectors.
      * Select your desired data source (e.g., "Text/CSV," "Azure Blob Storage," "SQL Server database," "Web API").
      * Provide the necessary connection details (server name, database, file path, credentials).
3.  **Select Data:**
      * Browse and select the specific tables, files, or folders you wish to ingest.
      * Preview the data to ensure you're connecting to the correct source and that the initial load looks as expected.

#### b. Phase 2: Transform Data (Using Power Query Editor)

Once the data is loaded into the Power Query Editor, you can apply a wide array of transformations. Power Query records each transformation as a "Applied Step," which can be reviewed, modified, or reordered.

**Common Transformation Examples:**

  * **Change Data Type:** Crucial for ensuring data quality and enabling correct calculations (e.g., changing text to number, date, or boolean).
  * **Remove Columns:** Eliminate unnecessary columns to optimize performance and simplify your dataset.
  * **Rename Columns:** Give columns more descriptive and user-friendly names.
  * **Filter Rows:** Remove rows based on specific conditions (e.g., filter out null values, specific dates, or categories).
  * **Merge Queries:** Combine data from two different queries (tables) based on a common column (similar to a SQL JOIN).
  * **Append Queries:** Stack rows from one query on top of another (similar to a SQL UNION).
  * **Add Custom Column:** Create new columns based on calculations or logic applied to existing columns using Power Query M language functions.
      * *Example:* `Date.Year([OrderDate])` to extract the year.
  * **Split Column:** Divide a single column into multiple columns based on a delimiter or number of characters.
  * **Group By:** Aggregate data based on one or more columns (e.g., calculate total sales per product category).
  * **Pivot/Unpivot Columns:** Reshape data from a wide format to a long format (unpivot) or vice-versa (pivot).

#### c. Phase 3: Set Data Destination

1.  **Add Data Destination:** After transforming your data, click "Add data destination" (or "Set data destination" in older versions) from the ribbon.
2.  **Choose Destination Type:**
      * **Lakehouse (Recommended for Fabric):** Choose your target Lakehouse within your workspace.
      * **Data Warehouse:** Select an existing Data Warehouse.
3.  **Configure Destination Table:**
      * Provide a name for the new table that will be created in your destination.
      * Select the "Load to new table" or "Load to existing table" option.
      * Confirm the schema and data types.
4.  **Publish:** Once configurations are complete, click "Publish" to save the Dataflow and trigger an initial data refresh. The data will be loaded into the specified destination table.

### 4\. Integrating Dataflows Gen2 and Pipelines

Dataflows Gen2 can be seamlessly integrated into Data Factory pipelines, allowing you to orchestrate them as part of larger data workflows.

#### a. Steps to Include a Dataflow in a Pipeline:

1.  **Create/Open a Pipeline:** Go to your Fabric Data Factory experience and create a new pipeline or open an existing one.
2.  **Add Dataflow Activity:** From the "Activities" pane, drag and drop the "Dataflow" activity onto the pipeline canvas.
3.  **Configure Dataflow Activity:**
      * In the "Settings" tab of the Dataflow activity, select the Dataflow Gen2 that you want to execute.
      * You can pass parameters to your Dataflow from the pipeline if your Dataflow is parameterized.
4.  **Run and Monitor Pipeline:**
      * Run the pipeline in "Debug" mode to test it.
      * "Publish" the pipeline to save changes.
      * Schedule the pipeline using a "Trigger" (e.g., daily, hourly) to automate data ingestion and transformation.
      * Monitor the pipeline's execution status and details in the "Monitor" hub of Microsoft Fabric.

### 5\. Exercise / Practice Points

  * Create a new Dataflow Gen2 in your Fabric workspace.
  * Connect to a sample data source (e.g., a public CSV file URL, a local CSV you upload to a Lakehouse file area).
  * Perform at least 3-5 different transformations using the Power Query editor (e.g., change data type, remove column, filter rows, add custom column, group by).
  * Set the data destination to a new table in your Lakehouse.
  * Publish the Dataflow and verify the data in your Lakehouse table.
  * Create a new Data Factory pipeline.
  * Add your Dataflow Gen2 as an activity in the pipeline.
  * Run the pipeline and monitor its execution.

This module equips you with the skills to use Dataflows Gen2 in Microsoft Fabric, enabling efficient, visual, and scalable data ingestion and preparation for your analytics needs.

### Sources:

  * [Ingest Data with Dataflows Gen2 in Microsoft Fabric - Training | Microsoft Learn](https://learn.microsoft.com/en-us/training/modules/use-dataflow-gen-2-fabric/)
  * [What is Dataflow Gen2? - Microsoft Fabric](https://learn.microsoft.com/en-us/fabric/data-factory/dataflows-gen2-overview)
  * [Quickstart: Create your first dataflow to get and transform data - Microsoft Fabric](https://www.google.com/search?q=https://learn.microsoft.com/en-us/fabric/data-factory/create-first-dataflow)
  * [Dataflow Gen2 concepts in Microsoft Fabric - Microsoft Fabric](https://www.google.com/search?q=https://learn.microsoft.com/en-us/fabric/data-factory/dataflows-gen2-concepts)
  * [Add a data destination - Microsoft Fabric](https://www.google.com/search?q=https://learn.microsoft.com/en-us/fabric/data-factory/dataflows-gen2-data-destination)
  * [Get data experience in Dataflow Gen2 - Microsoft Fabric](https://www.google.com/search?q=https://learn.microsoft.com/en-us/fabric/data-factory/dataflows-gen2-get-data)
  * [Use Dataflow Gen2 in pipelines - Microsoft Fabric](https://www.google.com/search?q=https://learn.microsoft.com/en-us/fabric/data-factory/dataflows-gen2-pipelines)
  * [Microsoft Fabric Dataflows Gen2 - YouTube](https://www.google.com/search?q=https://www.youtube.com/watch%3Fv%3Dfa4oQu--tHg%26list%3DPLMWaZteqtEaKPPXYSJcbJSvSumBzuKByd%26index%3D18)
  * [Microsoft Fabric Dataflows Gen2 - Introduction - YouTube](https://www.google.com/search?q=https://www.youtube.com/watch%3Fv%3Dfa4oQu--tHg%26list%3DPLMWaZteqtEaKPPXYSJcbJSvSumBzuKByd%26index%3D17)