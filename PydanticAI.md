It is a simple Data validation and Type Checking Libraray in Python
Pydantic is a Python library that helps us in defining and validating data models easily. When we build applications, that handle user input or data from various source
Data must be consisent and valid and  Pydantic makes this process easy by allowing us to define our data structure using Python classes and automatically validating the data against these structures.


Why we use pydantic:
- Automatically validates data based on type annotations.
- Data Parsing: Converts input data into Python objects with the correct types, mainly serailizing json.
- Error Handling: Provides clear and detailed error messages for invalid data.
- Field Validators: Allows custom validation logic with
- Pydantic is optimized for speed and supports optional Cython extensions for even faster performance.


```
Main Aim: to bring that FastAPI feeling to GenAI app development.
```
```Agent = LLM + Tools```

## how to create pydantic model 
1. Create a Data Model Using BaseModel->Start by importing BaseModel from pydantic.->Create a class that inherits from BaseModel.->Define attributes (fields) using Python type hints.

2. Once a model instance is created, its fields can be accessed and modified like normal Python class attributes.

3. We can define default values for fields. Fields without defaults are required.

4. To enforce custom rules, define a method and decorate it with @field_validator.

this is the basic way to implement pydantic






Common Use Cases of Pydantic: 
- API Data Validation and Parsing - Pydantic is widely used in APIs to validate incoming request data and parse it into the correct types.
- Data Processing Pipelines - Pydantic can be used in data processing pipelines to ensure data integrity and consistency across various stages.
- Configuration Management - Pydantic is ideal for managing application configurations, providing type-safe access to configuration data.