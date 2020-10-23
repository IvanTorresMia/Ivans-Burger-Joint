# Ivans-Burger-Joint


## Table of Contents
* [Description](#Description)
* [Technologies](#Technologies)
* [Features](#Features)
* [Author](#Author)
* [Credits](#Credits)
* [License](#License)

## Description 
Hi! Welcome to my Employee app. Here you are able to create a set of employees and the first thing you will be presented with after you install the app is a series of questions asking you information about your manager then giving you the option to add interns and or an engineer. Once you have answered the questions the app will render an html file for you! you will have a designed page with cards containing the information you entered about your employees. In the next few sections I will tell you how to install the app. 


## Technologies
* [JavaScript](https://www.w3schools.com/js/)
* [Inquirer](https://www.npmjs.com/package/inquirer)
* [FileSystem](https://nodejs.dev/learn/the-nodejs-fs-module)
* [Node.js](https://nodejs.org/en/)
* [Inquirer](https://www.npmjs.com/package/inquirer)


## Features
![Employee-gif](./assets/Employee-app-gif.gif2.gif)

* So After I used inwuire to prompt the user for a manager I called a function that asks what king of employee would they like to make. 
```
 inquirer.prompt(managerQuestions)
    .then(function(managerAnswers) {
        const manager = new Manager(managerAnswers.managersName, managerAnswers.managersId, managerAnswers.managersEmail, managerAnswers.managersOfficeNumber)
        employees.push(manager)
        kindOfEmployee();
    })
  ```


* Here is the function I call to ask the user what kind of employee they would like to make. Depending on their answer it will prompt them for either a intern or an engineew and push an new employee to an array. in the case that they say "none" then the app writes a new html file with the new employees.

```
const employees = [];

function kindOfEmployee() {
    inquirer.prompt(newEmployee)
        .then(function(newEmployeeAnswer) {
            if (newEmployeeAnswer.kindofTeamMember === "Engineer") {
                inquirer.prompt(engineersQuestions)
                    .then(function(engineerAnswers) {
                        const engineer = new Engineer(engineerAnswers.engineerName, engineerAnswers.engineerId, engineerAnswers.engineerEmail, engineerAnswers.engineerGithub);
                        employees.push(engineer)
                        kindOfEmployee()
                    })
            } else if (newEmployeeAnswer.kindofTeamMember === "Intern") {
                inquirer.prompt(internQuestions)
                    .then(function(internAnswers) {
                        const intern = new Intern(internAnswers.internsName, internAnswers.internsId, internAnswers.internsEmail, internAnswers.internsSchool);
                        employees.push(intern);
                        kindOfEmployee()
                    })
            } else if (newEmployeeAnswer.kindofTeamMember === "none") {
                const results = render(employees);
                fs.writeFile("./Develope/rendered.html", results,
                    function(err) {
                        if (err) throw err;
                        console.log("it worked!")

                    })
            }
        })
}
```



## Usage
[Usage-Video](https://drive.google.com/file/d/1LGy1IfXMMrCYD3GC1WQpJG-t-X_o8UCy/view)


## Installation
In order to run this app you have to install inquirer using 
```
mpi install inquirer
```
Then You intall "fs'

```
npm install fs
```

then to run you type 
```
node app.js
```

## Author
Ivan Torres
* [GitHub-Repo](https://github.com/IvanTorresMia/READme-project-Ivan)
* [linkedIn](www.linkedin.com/in/ivan-torres-0828931b2)

## Credits
* Credits for this homework assignment go out to Jerome, Manuel, Kerwin, Roger, and all of my classmates who helped me in study sessions. As well as my tutor who helped me a ton with understanding this homework assignment. 
* [StackOverFlow](https://stackoverflow.com/)




## License]
[MIT](https://choosealicense.com/licenses/mit/#) license 