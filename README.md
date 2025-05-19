# Lab_View_Report_Generation
In some environments, automating the measurement process can significantly streamline and simplify the creation of documentation. This repository contains a tool for automatically generating reports based on a .docx template. The report includes environmental data (temperature, humidity, pressure), information about the operator, the date and time of the test, as well as measurement results presented in the form of tables and charts. The entire solution was implemented in the LabVIEW environment, and the report generation utilizes an editable document template.

The report template looks as follows:
![image](https://github.com/user-attachments/assets/6e48daba-4f50-45db-8c82-d687dc298b6d)

Upon running the program, the report is filled out automatically.
![image](https://github.com/user-attachments/assets/fb70ec9f-7308-4128-8397-ac92c6093079)

The program has also been enhanced with numbering and generation of new reports, with an option to overwrite a specific file.
![image](https://github.com/user-attachments/assets/eb25b33d-bfe5-4943-9b83-b684c28ae372)

LabVIEW was chosen as the development environment due to its intuitive interface and quick integration capabilities with various measurement hardware. LabVIEW offers a wide range of dedicated libraries and ready-made drivers for popular devices such as Keysight or Rigol measurement instruments, significantly reducing the time required for system setup and commissioning. Programming in LabVIEW is done graphically by connecting dedicated functional blocks—which allows users to create complex processes without writing traditional textual code. This working model is especially userfriendly for those operating in engineering and laboratory environments. Another advantage is numerous ready examples and templates that facilitate quick startup and adaptation of existing solutions to individual needs. Thanks to this, users can create fully functional applications tailored to specific measurement requirements in a short time.
![image](https://github.com/Wneq1/Lab_View_Report_Generation/assets/127328405/eb07ee45-7ba1-4652-be3d-497dae79a13b)

The user interface was designed with clarity and intuitive operation in mind. The front panel features a START button that initiates the report generation process, as well as fields for manually entering necessary data such as humidity, pressure, temperature, and operator name. Additionally, a table with measurement data is visible, which is automatically populated during the program’s execution, along with a chart displaying live data, allowing quick monitoring of the measurement process in real time.

Below is an example of generating three independent variables and collecting them into a fourdimensional array, enabling advanced data analysis in the context of multiple parameters simultaneously. The results are presented clearly directly on the front panel, both in tabular and graphical form. The user also has the option to input selected variables manually via dedicated input fields in the program interface, allowing flexible testing of various measurement scenarios.
![generacja](https://github.com/user-attachments/assets/99462b4b-02b6-4602-ac9d-8cb1096fc8a7)

This part of the block diagram in LabVIEW is responsible for preparing and automatically filling the Word document template based on user input data and measurement results. Initially, the user inputs basic information—such as humidity, pressure, temperature, and operator name directly from the application front panel. These data are then passed to corresponding variables, which are embedded in the pre-prepared .docx template. It is important that the variable names in the code exactly match those defined in the document template both in content and case since only then will the data be correctly recognized and inserted in the right places.
![xD1](https://github.com/user-attachments/assets/25146ae7-a9c2-4f32-ac47-f8e9488e98cf)

The next step is automatically retrieving the current date and time, which are also inserted into the document template. Along the way, data is converted from string type to numeric format, and the data array is transposed to match the table structure requirements in the document. Simultaneously, a chart from the live measurements visible on the front panel—is generated and saved as an image file (e.g., JPG or BMP) in a designated folder. This graphic can later be embedded in the report as well.

Finally, the table in the Word document is filled based on the transformed data array. It is worth noting that data is entered starting from the second row the first row remains empty (or contains headers) which is a common practice when generating tables in text documents. The entire process is automated and executed by a single click of the “START” button on the application’s main panel.
![xd2](https://github.com/user-attachments/assets/750f6c87-3663-4485-84c2-05fae9d9a327)

This part of the program mainly handles the preparation and visualization of measurement data as a chart, which is then embedded in the Word document and saved as a graphic file. The process begins by assigning names to variables (e.g., T0 to T3), which are later used as labels for individual data series on the chart. Importantly, the zero index (T0) is not displayed on the chart to maintain clarity of presentation.

The program generates an XY Scatter Lines chart defined as “Scaled Graph,” where the user can specify the chart title, scaling (e.g., xScaleLinear), data size, and axis names—in this case, “Sample Number” for the X axis and “Amplitude” for the Y axis. Maximum values, axis colors, line style, and fill are configured manually or semi-automatically via dedicated control blocks. The block also allows detailed configuration of grid appearance and scale style (e.g., linear), enabling customization of the chart to meet user expectations or documentation standards.

Next, the chart image is generated by selecting the “create → reference” option from the front panel and connecting it to the appropriate block, then saved in the chosen disk location. The program automatically assigns the file name based on the path and iteration number. Simultaneously, a results table is created and inserted into the Word document, with data starting from the second row (the first usually contains headers). This entire block constitutes an integrated module responsible for the graphical representation of measurement data and its documentation.
