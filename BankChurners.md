# Project Name : Bank Churners
### Importing necessary libraries


```
import pandas as pd #allows importing data from various file formats such as comma-separated values, JSON, SQL, Microsoft Excel.
import matplotlib.pyplot as plt #To plot the data
```

### Reading BankChurners.csv file as bank_churners from the Data folder


```
bank_churners= pd.read_csv('Data/BankChurners.csv')
```

### Printing out first five rows from the file that we readed above


```
bank_churners.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CLIENT_NUM</th>
      <th>Attrition_Flag</th>
      <th>Customer_Age</th>
      <th>Gender</th>
      <th>Dependent_count</th>
      <th>Education_Level</th>
      <th>Marital_Status</th>
      <th>Income_Category</th>
      <th>Card_Category</th>
      <th>Months_on_book</th>
      <th>Total_Relationship_Count</th>
      <th>Months_Inactive_12_months</th>
      <th>Credit_Limit</th>
      <th>Total_Revolving_Bal</th>
      <th>Total_Trans_Amt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>768805383</td>
      <td>Existing Customer</td>
      <td>45</td>
      <td>M</td>
      <td>3</td>
      <td>High School</td>
      <td>Married</td>
      <td>$60K - $80K</td>
      <td>Blue</td>
      <td>39</td>
      <td>5</td>
      <td>1</td>
      <td>12691.0</td>
      <td>777</td>
      <td>1144</td>
    </tr>
    <tr>
      <th>1</th>
      <td>818770008</td>
      <td>Existing Customer</td>
      <td>49</td>
      <td>F</td>
      <td>5</td>
      <td>Graduate</td>
      <td>Single</td>
      <td>Less than $40K</td>
      <td>Blue</td>
      <td>44</td>
      <td>6</td>
      <td>1</td>
      <td>8256.0</td>
      <td>864</td>
      <td>1291</td>
    </tr>
    <tr>
      <th>2</th>
      <td>713982108</td>
      <td>Existing Customer</td>
      <td>51</td>
      <td>M</td>
      <td>3</td>
      <td>Graduate</td>
      <td>Married</td>
      <td>$80K - $120K</td>
      <td>Blue</td>
      <td>36</td>
      <td>4</td>
      <td>1</td>
      <td>3418.0</td>
      <td>0</td>
      <td>1887</td>
    </tr>
    <tr>
      <th>3</th>
      <td>769911858</td>
      <td>Existing Customer</td>
      <td>40</td>
      <td>F</td>
      <td>4</td>
      <td>High School</td>
      <td>Unknown</td>
      <td>Less than $40K</td>
      <td>Blue</td>
      <td>34</td>
      <td>3</td>
      <td>4</td>
      <td>3313.0</td>
      <td>2517</td>
      <td>1171</td>
    </tr>
    <tr>
      <th>4</th>
      <td>709106358</td>
      <td>Existing Customer</td>
      <td>40</td>
      <td>M</td>
      <td>3</td>
      <td>Uneducated</td>
      <td>Married</td>
      <td>$60K - $80K</td>
      <td>Blue</td>
      <td>21</td>
      <td>5</td>
      <td>1</td>
      <td>4716.0</td>
      <td>0</td>
      <td>816</td>
    </tr>
  </tbody>
</table>
</div>



### The datasheet contains 2000 rows and 15 columns


```
bank_churners.shape
```




    (2000, 15)




```
bank_churners.columns
```




    Index(['CLIENT_NUM', 'Attrition_Flag', 'Customer_Age', 'Gender',
           'Dependent_count', 'Education_Level', 'Marital_Status',
           'Income_Category', 'Card_Category', 'Months_on_book',
           'Total_Relationship_Count', 'Months_Inactive_12_months', 'Credit_Limit',
           'Total_Revolving_Bal', 'Total_Trans_Amt'],
          dtype='object')




```
print("There are total",bank_churners['Attrition_Flag'].nunique(),"attrition flag of customers.","\n")
print(bank_churners.Attrition_Flag.value_counts(),"\n")
```

    There are total 2 attrition flag of customers. 
    
    Existing Customer    1830
    Attrited Customer     170
    Name: Attrition_Flag, dtype: int64 
    
    


```
print("There are total",bank_churners['Card_Category'].nunique(),"types of card.","\n")
print(bank_churners.Card_Category.value_counts(),"\n")
```

    There are total 4 types of card. 
    
    Blue        1910
    Silver        75
    Gold          13
    Platinum       2
    Name: Card_Category, dtype: int64 
    
    


```
class details_of_each_column: # except column CLIENT_NUM
    
    def Attrition_Flag():
        print("There are total",bank_churners['Attrition_Flag'].nunique(),"attrition flag of customers.","\n")
        print(bank_churners.Attrition_Flag.value_counts(),"\n")
        
    def Customer_Age():
        print(bank_churners.Customer_Age.describe(),"\n")
        print("There are",(bank_churners.Customer_Age < 30).value_counts()[1], "clients with less than age of 30.")
        print("There are",((bank_churners.Customer_Age > 30)&(bank_churners.Customer_Age < 40)).value_counts()[1], "clients within (30 - 40) of age.")
        print("There are",((bank_churners.Customer_Age > 40)&(bank_churners.Customer_Age < 50)).value_counts()[1], "clients within (40 - 50) of age.")
        print("There are",((bank_churners.Customer_Age > 50)&(bank_churners.Customer_Age < 60)).value_counts()[1], "clients within (50 - 60) of age.")
        print("There are",((bank_churners.Customer_Age > 60)&(bank_churners.Customer_Age < 70)).value_counts()[1], "clients within (60 - 70) of age.")
        print("There are",(bank_churners.Customer_Age > 70).value_counts()[1], "clients with more than age of 70.")
        
    def Gender():
        print("There are total",bank_churners['Gender'].nunique(),"genders.","\n")
        print(bank_churners.Gender.value_counts(),"\n")
        
    def Dependent_count():
        print("There are total",bank_churners['Dependent_count'].nunique(),"dependent count of clients.","\n")
        print(bank_churners.Dependent_count.value_counts(sort=False),"\n")
        
    def Education_Level():
        print("There are total",bank_churners['Education_Level'].nunique(),"education level of clients.","\n")
        print(bank_churners.Education_Level.value_counts(),"\n")
    
    def Marital_Status():
        print("There are total",bank_churners['Marital_Status'].nunique(),"marital status of clients.","\n")
        print(bank_churners.Marital_Status.value_counts(),"\n")
        
    def Income_Category():
        print("There are total",bank_churners['Income_Category'].nunique(),"categories of income.","\n")
        print(bank_churners.Income_Category.value_counts(),"\n")
    
    def Card_Category():
        print("There are total",bank_churners['Card_Category'].nunique(),"types of card.","\n")
        print(bank_churners.Card_Category.value_counts(),"\n")
        
    def Months_on_book():
        print(bank_churners.Months_on_book.describe(),"\n")
        print("There are",(bank_churners.Months_on_book < 20).value_counts()[1], "clients with less than 20 months on book.")
        print("There are",((bank_churners.Months_on_book > 20)&(bank_churners.Months_on_book < 40)).value_counts()[1], "clients within (20 - 40) months on book.")
        print("There are",(bank_churners.Months_on_book > 40).value_counts()[1], "clients with more than 40 months on book.")
        
    def Total_Relationship_Count():
        print("There are total",bank_churners['Total_Relationship_Count'].nunique(),"relationship count of clients.","\n")
        print(bank_churners.Total_Relationship_Count.value_counts(sort=False),"\n")
    
    def Months_Inactive_12_months():
        print("There are total",bank_churners['Months_Inactive_12_months'].nunique(),"(inactive status for 12 months) of clients.","\n")
        print(bank_churners.Months_Inactive_12_months.value_counts(sort=False),"\n")
    
    def Credit_Limit():
        print(bank_churners.Credit_Limit.describe(),"\n")
        print("There are",(bank_churners.Credit_Limit < 10000.00).value_counts()[1], "clients with less than 10,000 credit limit.")
        print("There are",((bank_churners.Credit_Limit > 10000.00) & (bank_churners.Credit_Limit < 20000.00)).value_counts()[1], "clients within (10,000 - 20,000) credit limit.")
        print("There are",((bank_churners.Credit_Limit > 20000.00) & (bank_churners.Credit_Limit < 30000.00)).value_counts()[1], "clients within (20,000 - 30,000) credit limit.")
        print("There are",(bank_churners.Credit_Limit > 30000.00).value_counts()[1], "clients with more than 30,000 credit limit.")    
    
    def Total_Revolving_Bal():
        print(bank_churners.Total_Revolving_Bal.describe(),"\n")
        print("There are",(bank_churners.Total_Revolving_Bal < 1000.00).value_counts()[1], "clients with less than 1,000 total revolving balance.")
        print("There are",((bank_churners.Total_Revolving_Bal > 1000.00)&(bank_churners.Total_Revolving_Bal < 1500.00)).value_counts()[1], "clients within (1,000 - 1,500) total revolving balance.")
        print("There are",((bank_churners.Total_Revolving_Bal > 1500.00)&(bank_churners.Total_Revolving_Bal < 2000.00)).value_counts()[1], "clients within (1,500 - 2,000) total revolving balance.")
        print("There are",(bank_churners.Total_Revolving_Bal > 2000.00).value_counts()[1], "clients with more than 2,000 total revolving balance.")
        
    def Total_Trans_Amt():
        print(bank_churners.Total_Trans_Amt.describe(),"\n")
        print("There are",(bank_churners.Total_Trans_Amt < 1000.00).value_counts()[1], "clients with less than 1,000 total trans amount.")
        print("There are",((bank_churners.Total_Trans_Amt > 1000.00)&(bank_churners.Total_Trans_Amt < 1500.00)).value_counts()[1], "clients within (1,000 - 1,500) total trans amount.")
        print("There are",((bank_churners.Total_Trans_Amt > 1500.00)&(bank_churners.Total_Trans_Amt < 2000.00)).value_counts()[1], "clients within (1,500 - 2,000) total trans amount.")
        print("There are",((bank_churners.Total_Trans_Amt > 2000.00)&(bank_churners.Total_Trans_Amt < 2500.00)).value_counts()[1], "clients within (2,000 - 2,500) total trans amount.")
        print("There are",((bank_churners.Total_Trans_Amt > 2500.00)&(bank_churners.Total_Trans_Amt < 3000.00)).value_counts()[1], "clients within (2,500 - 3,000) total trans amount.")
        print("There are",((bank_churners.Total_Trans_Amt > 3000.00)&(bank_churners.Total_Trans_Amt < 3500.00)).value_counts()[1], "clients within (3,000 - 3,500) total trans amount.")
        print("There are",((bank_churners.Total_Trans_Amt > 3500.00)&(bank_churners.Total_Trans_Amt < 4000.00)).value_counts()[1], "clients within (3,500 - 4,000) total trans amount.")
        print("There are",((bank_churners.Total_Trans_Amt > 4000.00)&(bank_churners.Total_Trans_Amt < 4500.00)).value_counts()[1], "clients within (4,000 - 4,500) total trans amount.")
        print("There are",(bank_churners.Total_Trans_Amt > 4500.00).value_counts()[1], "clients with more than 4,500 total trans amount.")
        
```


```
details_of_each_column.Gender()
```

    There are total 2 genders. 
    
    M    1216
    F     784
    Name: Gender, dtype: int64 
    
    


```
print("There are total",bank_churners['Income_Category'].nunique(),"categories of income.","\n")
print(bank_churners.Income_Category.value_counts(),"\n")
print(bank_churners.Income_Category.value_counts().index.tolist(),"\n")
print(bank_churners.Income_Category.value_counts().tolist(),"\n")
```

    There are total 6 categories of income. 
    
    Less than $40K    546
    $80K - $120K      386
    $60K - $80K       362
    $40K - $60K       359
    Unknown           175
    $120K +           172
    Name: Income_Category, dtype: int64 
    
    ['Less than $40K', '$80K - $120K', '$60K - $80K', '$40K - $60K', 'Unknown', '$120K +'] 
    
    [546, 386, 362, 359, 175, 172] 
    
    


```
class visualization:
    def show_pie_chart():
        income_category_list = bank_churners['Income_Category'].value_counts().tolist()
        label_income_category = bank_churners.Income_Category.value_counts().index.tolist()
        exp = [0.2,0,0,0,0,0]
        plt.pie(income_category_list, labels = label_income_category, explode = exp , autopct = '%2.1f%%')
        plt.title("Income Category of Clients")
        plt.rcParams['font.size'] = 12.0
        plt.gcf().set_size_inches(6,6) 
        plt.show()
        
    def show_bar_graph():
        plt.style.use('dark_background')
        plt.title("Clients Inactive For 12 Months")
        plt.xlabel('12 Months Inactive')
        plt.ylabel('Number of Clients')
        bank_churners['Months_Inactive_12_months'].value_counts(sort= False).plot(kind='bar',edgecolor = 'yellow')
```


```
visualization.show_pie_chart()
```


    
![png](BankChurners_files/BankChurners_15_0.png)
    



```
visualization.show_bar_graph()
```


    
![png](BankChurners_files/BankChurners_16_0.png)
    



```
class tracer:
    def trace_client_background(): # tested code with characters,symbols,numbers
        while True:
            try:
                client_num = (int(input('Input a client number : ')))
                
                if client_num not in bank_churners.CLIENT_NUM.values:
                    print("No record found for the number : ",client_num,"\n\n")
                                                                                
                else:
                    print(bank_churners[bank_churners['CLIENT_NUM'] == client_num],"\n\n")
                        
            except ValueError:
                print("Please enter a valid client number...*OnlY IntEgerS*\n\n")
```


```
tracer.trace_client_background()
# testing output with strings, integers
#565676899
#843537503
#714804483
#abcd
#)_(+)
```

    Input a client number : hgh
    Please enter a valid client number...*OnlY IntEgerS*
    
    
    


    ---------------------------------------------------------------------------

    KeyboardInterrupt                         Traceback (most recent call last)

    <ipython-input-40-8acc6eede617> in <module>
    ----> 1 tracer.trace_client_background()
          2 # testing output with strings, integers
          3 #565676899
          4 #843537503
          5 #714804483
    

    <ipython-input-39-aa1bc16ca75a> in trace_client_background()
          3         while True:
          4             try:
    ----> 5                 client_num = (int(input('Input a client number : ')))
          6 
          7                 if client_num not in bank_churners.CLIENT_NUM.values:
    

    ~\anaconda3\lib\site-packages\ipykernel\kernelbase.py in raw_input(self, prompt)
        858                 "raw_input was called, but this frontend does not support input requests."
        859             )
    --> 860         return self._input_request(str(prompt),
        861             self._parent_ident,
        862             self._parent_header,
    

    ~\anaconda3\lib\site-packages\ipykernel\kernelbase.py in _input_request(self, prompt, ident, parent, password)
        902             except KeyboardInterrupt:
        903                 # re-raise KeyboardInterrupt, to truncate traceback
    --> 904                 raise KeyboardInterrupt("Interrupted by user") from None
        905             except Exception as e:
        906                 self.log.warning("Invalid Message:", exc_info=True)
    

    KeyboardInterrupt: Interrupted by user



```
!jupyter nbconvert --to markdown LinerR.ipynb
```

    This application is used to convert notebook files (*.ipynb) to various other
    formats.
    
    WARNING: THE COMMANDLINE INTERFACE MAY CHANGE IN FUTURE RELEASES.
    
    Options
    =======
    The options below are convenience aliases to configurable class-options,
    as listed in the "Equivalent to" description-line of the aliases.
    To see all configurable class-options for some <cmd>, use:
        <cmd> --help-all
    
    --debug
        set log level to logging.DEBUG (maximize logging output)
        Equivalent to: [--Application.log_level=10]
    --generate-config
        generate default config file
        Equivalent to: [--JupyterApp.generate_config=True]
    -y
        Answer yes to any questions instead of prompting.
        Equivalent to: [--JupyterApp.answer_yes=True]
    --execute
        Execute the notebook prior to export.
        Equivalent to: [--ExecutePreprocessor.enabled=True]
    --allow-errors
        Continue notebook execution even if one of the cells throws an error and include the error message in the cell output (the default behaviour is to abort conversion). This flag is only relevant if '--execute' was specified, too.
        Equivalent to: [--ExecutePreprocessor.allow_errors=True]
    --stdin
        read a single notebook file from stdin. Write the resulting notebook with default basename 'notebook.*'
        Equivalent to: [--NbConvertApp.from_stdin=True]
    --stdout
        Write notebook output to stdout instead of files.
        Equivalent to: [--NbConvertApp.writer_class=StdoutWriter]
    --inplace
        Run nbconvert in place, overwriting the existing notebook (only 
        relevant when converting to notebook format)
        Equivalent to: [--NbConvertApp.use_output_suffix=False --NbConvertApp.export_format=notebook --FilesWriter.build_directory=]
    --clear-output
        Clear output of current file and save in place, 
        overwriting the existing notebook.
        Equivalent to: [--NbConvertApp.use_output_suffix=False --NbConvertApp.export_format=notebook --FilesWriter.build_directory= --ClearOutputPreprocessor.enabled=True]
    --no-prompt
        Exclude input and output prompts from converted document.
        Equivalent to: [--TemplateExporter.exclude_input_prompt=True --TemplateExporter.exclude_output_prompt=True]
    --no-input
        Exclude input cells and output prompts from converted document. 
        This mode is ideal for generating code-free reports.
        Equivalent to: [--TemplateExporter.exclude_output_prompt=True --TemplateExporter.exclude_input=True]
    --allow-chromium-download
        Whether to allow downloading chromium if no suitable version is found on the system.
        Equivalent to: [--WebPDFExporter.allow_chromium_download=True]
    --log-level=<Enum>
        Set the log level by value or name.
        Choices: any of [0, 10, 20, 30, 40, 50, 'DEBUG', 'INFO', 'WARN', 'ERROR', 'CRITICAL']
        Default: 30
        Equivalent to: [--Application.log_level]
    --config=<Unicode>
        Full path of a config file.
        Default: ''
        Equivalent to: [--JupyterApp.config_file]
    --to=<Unicode>
        The export format to be used, either one of the built-in formats
        ['asciidoc', 'custom', 'html', 'latex', 'markdown', 'notebook', 'pdf',
        'python', 'rst', 'script', 'slides', 'webpdf'] or a dotted object name that
        represents the import path for an `Exporter` class
        Default: ''
        Equivalent to: [--NbConvertApp.export_format]
    --template=<Unicode>
        Name of the template to use
        Default: ''
        Equivalent to: [--TemplateExporter.template_name]
    --template-file=<Unicode>
        Name of the template file to use
        Default: None
        Equivalent to: [--TemplateExporter.template_file]
    --writer=<DottedObjectName>
        Writer class used to write the  results of the conversion
        Default: 'FilesWriter'
        Equivalent to: [--NbConvertApp.writer_class]
    --post=<DottedOrNone>
        PostProcessor class used to write the results of the conversion
        Default: ''
        Equivalent to: [--NbConvertApp.postprocessor_class]
    --output=<Unicode>
        overwrite base name use for output files. can only be used when converting
        one notebook at a time.
        Default: ''
        Equivalent to: [--NbConvertApp.output_base]
    --output-dir=<Unicode>
        Directory to write output(s) to. Defaults to output to the directory of each
        notebook. To recover previous default behaviour (outputting to the current
        working directory) use . as the flag value.
        Default: ''
        Equivalent to: [--FilesWriter.build_directory]
    --reveal-prefix=<Unicode>
        The URL prefix for reveal.js (version 3.x). This defaults to the reveal CDN,
        but can be any url pointing to a copy  of reveal.js.
        For speaker notes to work, this must be a relative path to a local  copy of
        reveal.js: e.g., "reveal.js".
        If a relative path is given, it must be a subdirectory of the current
        directory (from which the server is run).
        See the usage documentation
        (https://nbconvert.readthedocs.io/en/latest/usage.html#reveal-js-html-
        slideshow) for more details.
        Default: ''
        Equivalent to: [--SlidesExporter.reveal_url_prefix]
    --nbformat=<Enum>
        The nbformat version to write. Use this to downgrade notebooks.
        Choices: any of [1, 2, 3, 4]
        Default: 4
        Equivalent to: [--NotebookExporter.nbformat_version]
    
    Examples
    --------
    
        The simplest way to use nbconvert is

    [NbConvertApp] WARNING | pattern 'LinerR.ipynb' matched no files
    

    
        
        > jupyter nbconvert mynotebook.ipynb --to html
        
        Options include ['asciidoc', 'custom', 'html', 'latex', 'markdown', 'notebook', 'pdf', 'python', 'rst', 'script', 'slides', 'webpdf'].
        
        > jupyter nbconvert --to latex mynotebook.ipynb
        
        Both HTML and LaTeX support multiple output templates. LaTeX includes
        'base', 'article' and 'report'.  HTML includes 'basic' and 'full'. You
        can specify the flavor of the format used.
        
        > jupyter nbconvert --to html --template lab mynotebook.ipynb
        
        You can also pipe the output to stdout, rather than a file
        
        > jupyter nbconvert mynotebook.ipynb --stdout
        
        PDF is generated via latex
        
        > jupyter nbconvert mynotebook.ipynb --to pdf
        
        You can get (and serve) a Reveal.js-powered slideshow
        
        > jupyter nbconvert myslides.ipynb --to slides --post serve
        
        Multiple notebooks can be given at the command line in a couple of 
        different ways:
        
        > jupyter nbconvert notebook*.ipynb
        > jupyter nbconvert notebook1.ipynb notebook2.ipynb
        
        or you can specify the notebooks list in a config file, containing::
        
            c.NbConvertApp.notebooks = ["my_notebook.ipynb"]
        
        > jupyter nbconvert --config mycfg.py
    
    To see all available configurables, use `--help-all`.
    
    


```

```
