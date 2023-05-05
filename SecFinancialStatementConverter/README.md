# SecFinancialStatementConverter
The converter can be used to convert the Financial [Statement Data Sets](https://www.sec.gov/dera/data/financial-statement-data-sets) of the Sec. The files are provided each quarter by the Sec. The mapping of the Cik keys to the ticker Symbols is done with this Sec [ticker.txt](https://www.sec.gov/include/ticker.txt). The Jupyter notebook can be used to convert to Sec data in a Json format that can be imported easily. An example for an import can be found in the [AngularPortfolioMgr](https://github.com/Angular2Guy/AngularPortfolioMgr) project. The [documentation](https://www.sec.gov/files/aqfs.pdf) about the values of the data can be found at the Sec website.

## Json files and format
The Sec data is provided in a structure of 3 marshaled Json objects. The first provides the data about the company that filed the the report.

`{"quarter": "FY", "country": "US", "data": {}, "year": 2009, "name": "SOUTHERN CALIFORNIA EDISON CO", "startDate": "2009-12-31", "endDate": "2010-12-30", "symbol": "SCE-PG", "city": "ROSEMEAD"}`

The data property contains the values, that are ignored in this example.

The second structures the values in the cashflow, balancesheet, income arrays. 

`{"cf": [], "bs": [], "ic": []}`

The array values are ignored in this example.

The third are the value objects that are contained in the arrays.

`{"info": "Total long-term assets", "unit": "USD", "label": "Sum of the carrying amounts as of the balance s...", "concept": "LongTermAssets", "value": 5852000000}`

The concepts in the object are defined by the Sec and are keys that can be found in many reports and can be analysed.

## Converting a Sec file
To convert a Sec file it has to be put in the importFiles folder and the ticker.txt has to be present too. Then the Jupyter notebook has to be updated with the new filename and the output directory should be set(the filename for example). The Sec files are zipped and large and interdepended. That causes longer runtimes of the converter(depending on your cpu minutes to hours). After the Jupyter Notebook has finished the result directory/ies can be zipped with this command in the exportFiles folder: "zip -r9 export.zip *" to get a "export.zip" file.

## Articles
* [Using a Jupyter Notebook with Pandas for data conversion](https://angular2guy.wordpress.com/2023/05/05/using-a-jupyter-notebook-with-pandas-for-data-conversion/)
