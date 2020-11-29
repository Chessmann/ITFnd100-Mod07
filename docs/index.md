# Title, Date
**Dev:** *Chessmann*  
## Introduction
```
# ------------------------------------------------- #
# Title: Lab7-1
# Description: A simple example of storing data in a binary file
# ChangeLog: (Who, When, What)
# <YourName>,<1.1.2030>,Created Script
# ------------------------------------------------- #
import pickle  # This imports code from another code file!

# Data -------------------------------------------- #
strFileName = 'AppData.dat'
lstCustomer = []

# Processing -------------------------------------- #
def save_data_to_file(file_name, lstCustomer):
    objFile = open("AppData.dat", "ab")
    pickle.dump(lstCustomer, objFile)
    objFile.close()


def read_data_from_file(file_name):
    objFile = open("AppData.dat", "rb")
#    for row in strFileName:
    objFileData = pickle.load(objFile)  # load() only loads one row of data.
    objFile.close()


# Presentation ------------------------------------ #
print('Here is the ID and Name from the file: ')
lstCustomer = read_data_from_file(file_name=strFileName)
print(objFile)
## Topic 1
### Subtopic
## Summary
