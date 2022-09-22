# Overview 

```mermaid
flowchart LR

    name1 & name2 --> name3
    name4 --> name5
```

### do_something
**INPUTS:**
    - name1
    - name2

 certainly does something 

#### Code
```python
    @transform(
        someclass,
        Input('name1','dbfs://location1') 
        +  Input('name2','dbfs://location2') 
        >> Output('name3','dbfss://location3')    
    )
    def do_something(self,**context):
        """ certainly does something """
        print(context['name1'].location)

```

### do_something_else
**INPUTS:**
    - name4

 takes in some adls stuff and transforms it  

#### Code
```python
    @transform(
        someclass,
        Input('name4','dbfss://location_nowhere')
        >> Output('name5','dbfss://location_somewhere')
    )
    def do_something_else(self,**context):
        """ takes in some adls stuff and transforms it  """
        print(context)

```







# something Overview 
None

```mermaid
flowchart LR

    input_name --> output name
```

### source_to_bronze
**INPUTS:**
    - input_name


        This method is designed to bring in data from an external source to the Bronze Alchemy layer

        access input and output objects through context i.e. 
        >>> context["<input name>"].location 
        --> "<adls path>"
        
        Args:
            None
            
        Returns: 
            None
        

#### Code
```python
    @transform(
        BaseMedallion,
        Input('input_name', '<adls path>')
        # + <other input objects>
        >> Output('output name', '<adls path>')
    )
    def source_to_bronze(self,**context) -> None:
        """
        This method is designed to bring in data from an external source to the Bronze Alchemy layer

        access input and output objects through context i.e. 
        >>> context["<input name>"].location 
        --> "<adls path>"
        
        Args:
            None
            
        Returns: 
            None
        """
        self.logger.info(f"Source data written to {self.bronze_path}")

```
