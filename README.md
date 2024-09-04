
# DataWeave Local Project

Welcome to my local **DataWeave** project! This repository is a workspace for running and experimenting with **DataWeave** mappings locally using the [DataWeave extension for VSCode](https://developer.mulesoft.com/tutorials-and-howtos/dataweave/dataweave-extension-vscode-getting-started/).

DataWeave is the powerful data transformation language of MuleSoft, and with this setup, you can run DataWeave scripts directly on your local machine, test various mappings, and transform data easily.

## Features

- 🛠️ **Run DataWeave scripts locally** – No need for MuleSoft servers, you can execute scripts right on your local environment.
- 🗂️ **Test various mappings** – Work with different data formats like JSON, XML, CSV, etc.
- 💻 **Full integration with VSCode** – Utilize the DataWeave extension to take advantage of syntax highlighting, formatting, and testing tools.
- 🔄 **Easy data transformations** – Write and test your DataWeave mappings with live feedback.

## Getting Started

### Prerequisites

Make sure you have the following installed on your system:

- [Visual Studio Code (VSCode)](https://code.visualstudio.com/)
- [DataWeave Extension for VSCode](https://marketplace.visualstudio.com/items?itemName=MuleSoftInc.dataweave)
- Java **version 8** (required for running DataWeave engine locally)
- Maven version **3.6.3 or higher**

### Installation

1. **Clone this repository** to your local machine:

   ```bash
   git clone https://github.com/yourusername/dataweave-local-project.git
   ```

2. **Open the project in VSCode**:

   ```bash
   cd dataweave-local-project
   code .
   ```

3. **Install the DataWeave Extension**:
   
   Follow the steps [here](https://developer.mulesoft.com/tutorials-and-howtos/dataweave/dataweave-extension-vscode-getting-started/) to install and configure the DataWeave extension in VSCode.

### Running DataWeave Mappings Locally

1. **Write your DataWeave mappings**:
   Create or edit `.dwl` files within the projects `src/main/dw` folder to define your transformations.

2. **Execute the mappings**:
   To run the DataWeave script locally, right-click on the `.dwl` file in VSCode and select `Run DataWeave Script`. Alternatively, use the command palette (`Ctrl + Shift + P`) and select `Run DataWeave Script` or right click in your `.dwl` file and choose `DataWeave: Enable AutoPreview`

3. **View the output**:
   Once the script runs, the transformed output will be displayed directly in VSCode's terminal or output panel.

## Project Structure

```bash
dataweave-local-project/
├── src/                                         # Source directory for the project
     ├── main/                                   # Main application code directory
           ├── dw/                               # Folder for your DataWeave (.dwl) mappings
                ├── main.dwl                     # DataWeave mapping file
     ├── test/                                   # Directory for test-related files
           ├── resources/                        # Resources for testing
                 ├── main/PlayGround/inputs/     # Folder for main.dwl inputs
                       ├── payload.json          # Input payload for main.dwl
                       ├── vars.json             # Variables for main.dwl
├── target/                                      # Directory for build outputs and artifacts
├── pom.xml                                      # Maven project configuration file
└── README.md                                    # This readme file
```

## Example Usage

Suppose you have an input file `payload.json` in folder `src/test/resources/transform/Playground/inputs` like this:

```json
{
  "name": "John",
  "age": 30
}
```

You can write a DataWeave mapping in a file `transform.dwl` in folder `src/main/dw` as follows:

```dwl
%dw 2.0
output application/json
var person = payload
---
{
  fullName: person.name,
  ageInFiveYears: person.age + 5
}
```

Run the script, and the output will be:

```json
{
  "fullName": "John",
  "ageInFiveYears": 35
}
```
