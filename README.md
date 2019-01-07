# CPP-JSON

## Prerequisite
1. Visual Studio
2. [Nlohmann Json Library](https://github.com/nlohmann/json)

JSON implementation is straightforward and reading its ReadMe will explain everything.

It contains a single file to allow json file to be manipulated in C++. To integrate it,
go to the project in visual studio and go to **"Project" -> "Properties" -> "C/C++"
-> "Additional Include Directories"** and add **"single_include"** from the nlohmann folder.
To use the library in your code, add:

`#include <nlohmann\json.hpp>`<br>
`using json = nlohmann::json;`

## How to Load in Json File

1. include i/o file: <br>
    `include <fstream>;`
2. load the file:<br>
    `std::ifstream jsonFile("filePath.json");`
3. load the information:<br>
    `json fileInformation = json::parse(jsonFile);`
4. access the information:<br>
    for numbers...<br>
    `fileInformation["parentName"]`<br>
    for strings...<br>
    `fileInformation["parentName"].get<std::string>()`<br>
    for child...<br>
    `fileInformation["/parentName/childName"_json_pointer]`

## How to Write to Json file
writing to json file:<br>
`json fileInformation;`

1. one element at a time...<br>
`fileInformation["parentName1"] = value1;`
`fileInformation["/parentName2/childName1/"_json_pointer] = value2;`
2. everything in a string...<br>
`fileInformation = json::parse("{
  \"parentName1\" : \"childName1\" ,
  \"parentName2\" : \"childName2\" ,
  \"parentName3\" : {
  \"childName3\":\"grandchildrenName3\"}}");`<br>
open file...<br>
`std::ofstream jsonFile("filePath");`<br>
save to file...<br>
`jsonFile << fileInformation;`<br>
close file...<br>
`jsonFile.close();`

## How to convert Json format to String format

`std::string s = fileInformation.dump(4) // where the 4 is the size of indent`


Few works that uses nlohmann json:

- [CPP-NODE-WS](https://github.com/Omniphics/CPP-NODE-WS) - also has an explanation of usage
- [Depth-Sensor](https://github.com/Omniphics/Depth-Sensor)
