# A Pipeline Architecture to Obtain Software Requirements and Specifications Documentation by Using Generative Artificial Intelligence

This repository serves two main functions: firstly, it contains the outputs generated as a result of the experiment undertaken during the course of the related master's thesis. Secondly, it also details the removal of comments from the sample codebase.

---

## Output
The outputs of the experiments are contained within the `output` directory at the root of this repository. The outputs themselves are raw data obtained from the models under test.

Each file is named to reflect both:
- the model used, and  
- the specific experiment run that generated the output

This enables us to ascertain the purpose of an output by looking at its file name.

---

## Removing Comments

The codebase used in the experiments is available at the [DDDsample-core repository](https://github.com/citerus/dddsample-core).  

To remove the comments from the JAVA files, we will use both regular expressions and [Notepad++](https://notepad-plus-plus.org/).

### Step-by-step instructions

1. **Download the repository**

   > Clone or download the DDDsample repository.

2. **Navigate to the source directory**

   > `\dddsample-core-master\src\main\java\se\citerus\dddsample`
3. **Open file in Notepad++**
   > Open `Application.java` using Notepad++.

4. **Open the “Find in Files” dialog**
   > - Go to **Search → Find...**
   > - Switch to the **Find in Files** tab

5. **Configure the search**
   > - **Find what [[1][1], [2][2]]:**
   > ```
   > \/\/.*$|\/\*[\s\S]*?\*\/
   > ```
   > - **Replace with:** *(leave empty)*
   > - **Filters:**
   > ```
   > *.java
   > ```
   > - **Directory:**
   > ```
   > \dddsample-core-master\src\main\java\se\citerus\dddsample
   > ```
   > - Enable:
   > - [x] In all sub-folders  
   > - [x] Regular expression  

6. **Remove Comments**

   > Run the `Replace in Files` operation to remove comments from all Java files.

### Sample Image

<img width="960" height="343" alt="image" src="https://github.com/user-attachments/assets/8995fae7-384c-4e19-9d8a-992907681700" />
The sample image shows us interacting with Notepad++.

---

## Running the Application

After removing the comments, the project can be imported into an IDE and executed using:

```bash
mvn spring-boot:run
```
The application will then be available at [localhost:8080](http://localhost:8080/dddsample).

---

## Important Notes and Limitations

It has to be mentioned that the given regex is not usable for all JAVA code bases [[1][1], [2][2]]. It works for our case, but there are some cases where we will remove legitimate code. For example:

```java
String s = "this is not // a comment";
```

In such a case we would remove valid code.

---

## References
[1] https://stackoverflow.com/questions/28411032/java-regex-remove-comments

[2] https://stackoverflow.com/questions/14975737/regular-expression-to-remove-comment

[1]: https://stackoverflow.com/questions/28411032/java-regex-remove-comments
[2]: https://stackoverflow.com/questions/14975737/regular-expression-to-remove-comment
