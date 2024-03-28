---
  layout: default.md
  title: "User Guide"
  pageNav: 3
---

# Avengers Assemble User Guide

Avengers Assemble (AA) is a **desktop app designed to simplify contact management**. It is meant for use with a Command Line Interface (CLI) 
while still having the benefits of a Graphical User Interface (GUI). 

This application is designed for **Head Tutors** of the NUS CS1101S Programming Methodology course,
enabling you to streamline your administrative tasks related to contact management with students, fellow teaching assistants, and course instructors.

This user guide provides a comprehensive overview of the Avengers Assemble's features and functionalities, 
and aims to guide you through its setup and usage. 
We will walk you through each feature in a structured manner:

1. Installation,
2. Basic commands like adding and editing, and
3. Advanced commands like filtering and exporting of data.

By following this guide, you will be able to gain a thorough understanding of Avengers Assemble and maximize its potential to streamline your administrative tasks.
<br>

<!-- * Table of Contents -->

--------------------------------------------------------------------------------------------------------------------

## Quick Start

1. Ensure you have `Java 11` or above installed in your computer.

2. Download the latest `avengersassemble.jar` [here](https://github.com/AY2324S2-CS2103T-T10-1/tp/releases/tag/v1.2).

3. Copy the file to the folder you want to use as the _home folder_ for our application.

4. On a command terminal, `cd` into the folder you put the jar file in, and use the `java -jar avengersassemble.jar` command to run the application.<br>
   ```dtd
    cd <path_to_the_folder_containing_the_jar_file>
    java -jar avengersassemble.jar
    ```
   You should see this when the app starts up. Note that it contains some sample data when you first run it.<br>

<img src="images/Ui.png" alt="image of Avengers Assemble's UI">

5. Refer to the [features](#features) below for details of each command.

--------------------------------------------------------------------------------------------------------------------

## Legend
These boxes might offer you additional information of different types:

> **Good to know:**
> Provides you with supporting information.

<box type="info" seamless>

**Important:**
Provides you with more important information that you should know.
</box>

<box type="tip" seamless>

**Tip:**
Provides you with tips to use our app more effectively.
</box>

<box type="warning" seamless>

**Caution:**
Provides you with warnings about potential issues you might face.
</box>

## Features

### Getting Help : `help`

Shows you a link to guide you on how to use the application. Click on the link to access the user guide.

<p align="center">
    <img src="images/helpMessage.png" alt="image of help message window" width="500">
</p>

**Format:** `help`
> **Note:** The application ignores any extraneous parameters i.e. `help 123` will be interpreted as `help` by Avengers Assemble.

<br>

Before we proceed with the commands, here are some important points to note on their formatting. These points will also be repeated in the [command format summary](#command-format-summary) for you to refer to easily at any point in time.

<box type="info" seamless>

**Important:** </br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
  > e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

* Prefixes encased with '[ ]' are optional.
  > e.g. `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Prefixes with '…' after them can be used multiple times.
  > e.g. `[t/TAG]…​` can be used as ` ` (i.e. 0 times), `t/friend` (i.e 1 time), `t/friend t/family` etc.

* Parameters can be in any order.<br>
  > e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

* Extraneous parameters for commands that do not take in parameters (such as `help` , `list`, `exit`, `copy`, `export` and `clear`) will be ignored.<br>
  > e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</box>

<box type="warning" seamless>

**Caution:** </br>
* If you are using a PDF version of this document, be careful when copying and pasting commands that span multiple lines as space characters surrounding line-breaks may be omitted when copied over to the application.

</box>
<br>

### Adding a Person: `add`

Adds a person to your contact list. The person's details are now stored in the application.

**Format:** `add n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS [t/TAG]… [m/MATRICULATION_NUMBER] [s/STUDIO] [r/REFLECTION]​`

**Example:**
`add n/John Doe p/98765432 e/johnd@example.com a/John street, block 123, #01-01 m/A1234567Z s/S1 r/R2`<br>

Adds a contact John Doe with the respective phone number, email and physical addresses, matriculation number, studio group and recitation group.

<box type="info" seamless>

**Important:** Each person should have a unique email address. Avengers Assemble does not allow for duplicate email addresses to be added.

</box>

<box type="tip" seamless>

**Tip:** A person can have any number of tags (including 0)
</box>

> **Note:** The following tags will be automatically added to the person if the following conditions are met:
> 1. `student`: If matriculation number, studio, and reflection fields are present;
> 2. `TA`: If matriculation number and one of either studio or reflection fields are present;
> 3. `instructor`: If none of the three fields are present.
> 
> You are free to edit or remove the tags after the person is added using the [`edit`](#editing-a-person--edit) feature.

For more details on each parameter, [click here](#command-format-summary).

<br>

### Listing All Persons : `list`

Displays all the persons in your contact list.

**Format:** `list`
> **Note:** The application ignores any extraneous parameters i.e. `list 123` will be interpreted as `list` by Avengers Assemble.

<br>

### Editing a Person : `edit`

Edits the details of an existing person in your contact list.

**Format:** `edit INDEX [n/NAME] [p/PHONE] [e/EMAIL] [a/ADDRESS] [t/TAG]… [m/MATRICULATION_NUMBER] [s/STUDIO] [r/REFLECTION]​`

<box type="info" seamless>

**Information:** <br>
* The person at the specified `INDEX` will be edited. The index **must be a positive integer** (1, 2, 3, …)​
* At least one of the optional fields must be provided.
* Existing values will be updated to the new values.
* Editing tags will replace all existing tags i.e. adding of tags is **not cumulative**.
* You can remove optional fields by typing `t/`, `m/`, `r/` or `s/` respectively without any values.

</box>

**Examples:**

1. `edit 2 n/Betsy Crower t/`: <br>
   * Edits the name of the 2nd person to be `Betsy Crower` and clears all existing tags.

2. `edit 1 p/91234567 e/johndoe@example.com`: <br>
   * Edits the phone number and email address of the 1st person to be `91234567` and `johndoe@example.com` respectively.

<box type="info" seamless>
  
**Important:**

Updating a matriculation number, studio, or reflection field will not automatically update the tags of the person. You will need to manually update the tags if necessary.

</box>

For more details on each parameter, [click here](#command-format-summary).

<br>

### Filtering Persons: `find`

Filters your contacts based on specific criteria you set.

**Format:** `find PREFIX/KEYWORD`

<box type="info" seamless>

**Information:** <br>
* Use this command to search for persons using a specific aspect of their details, as specified by the prefix.
* The search will return any result that contains the keyword you have specified. 
    > e.g. `find e/john` will find any person that contains `john` in their email.
* The search is **case-insensitive** i.e. `john` and `John` are interpreted to be the same.
* Only one prefix can be used at a time.

</box>

**Example:** `find n/John` 

displays all contacts with the name containing `John` in your contact list. 

For more details on each parameter, [click here](#command-format-summary).

<br>

### Copying Contact Details: `copy`

Copies the emails of currently displayed persons into your clipboard.

**Steps:**
1. Filter out the persons you would like to email using the [`find`](#filtering-persons--find) or [`list`](#listing-all-persons--list) command.
2. Type `copy` to copy the emails of the currently listed persons to your clipboard.
3. The emails will be copied into your clipboard such that you may easily broadcast emails
   to specific groups of people.

**Format:** `copy`
>Note: The application ignores any extraneous parameters i.e. `copy 123` will be interpreted as `copy` by Avengers Assemble.

<br>

### Deleting a Person : `delete`

Deletes the specified person from your contact list.

**Format:** `delete INDEX`

* Deletes the person at the specified `INDEX`.
* The index refers to the index number shown in the displayed person list.
* The index **must be a positive integer** 1, 2, 3, …​

**Examples:**
* `list` followed by `delete 2` deletes the second person displayed in Avengers Assemble.
* `find Betsy` followed by `delete 1` deletes the first person in the results of the `find` command.

<br>

### Deleting All Filtered Persons : `deleteshown`

Deletes the current filtered list of persons. Requires a `find` command to be run first.

**Steps:**
1. Use the [`find`](#filtering-persons--find) command to filter out the list of persons you want to delete.
2. Type `deleteshown` to delete all persons in the current filtered list of persons.

**Format:** `deleteshown`
>Note: The application ignores any extraneous parameters i.e. `deleteshown 123` will be interpreted as `deleteshown` by Avengers Assemble.

<br>

### Clearing All Entries : `clear`

Clears **all** entries from your contact list.

Format: `clear`
> **Note:** The application ignores any extraneous parameters i.e. `clear 123` will be interpreted as `clear` by Avengers Assemble.

<br>

### Exporting Data to a CSV file : `export`

Exports currently listed persons and their details to a CSV file, avengersassemble.csv, which can be found in addressbookdata.

**Steps:**
1. Filter out the persons you want to export using the [`find`](#filtering-persons--find) or 
[`list`](#listing-all-persons--list) command.
2. Type `export` to export the currently listed persons and their details to a CSV file.
3. Upon export, a folder named addressbookdata will be created in the same directory where Avengers Assemble is located. Within this folder, you'll find the CSV file named avengersassemble.csv, containing the exported data.

**Format:** `export`

> **Note:** The application ignores any extraneous parameters i.e. `export 123` will be interpreted as `export` by Avengers Assemble.

<box type="info" seamless>

**Important:** When performing an export, the current information will overwrite the existing CSV file named avengersassemble.csv located within the addressbookdata folder.
A new CSV file will not be created with each export.

Users have the option to manually move the current CSV file out of the addressbookdata folder if they do not want the information to be overwritten in the next export.
A new CSV file of the same name in the same location will again be created when performing the next export.

</box>

<br>

### Importing Data from a CSV File : `import`

Imports all persons and their details from a CSV file of your specification.

**Format:** `import i/FILEPATH`

<box type="info" seamless>

**Important:**<br>
The file path should be **absolute**.

</box>

**Example:** `import i/C:/Users/alk/Downloads/avengersassemble.csv` 

imports the data from the CSV file located at `C:/Users/alk/Downloads/avengersassemble.csv`.


For more details on the input parameter, [click here](#command-format-summary).

<br>

### Exiting the Program : `exit`

Exits the program. The app will close automatically.

**Format:** `exit`

>Note: The application ignores any extraneous parameters i.e. `exit 123` will be interpreted as `exit` by Avengers Assemble.

--------------------------------------------------------------------------------------------------------------------

## Additional Information

### Saving the Data

All data are saved in the hard disk automatically after any command that changes the data. There is no need to save manually.

### Editing the Data File

All data are saved automatically as a JSON file located at `[JAR file location]/data/avengersassemble.json` by default. You can update data directly by editing that data file if you are an advanced user.

<box type="warning" seamless>

**Caution:**
If your changes to the data file makes its format invalid, Avengers Assemble will discard all data and start with an empty data file at the next run.  Hence, it is recommended to take a backup of the file before editing it.<br/>
Furthermore, certain edits can cause the Avengers Assemble application to behave in unexpected ways (e.g., if a value entered is outside the acceptable range). Therefore, edit the data file only if you are confident that you can update it correctly.
</box>

--------------------------------------------------------------------------------------------------------------------

## FAQ

**Q**: How do I transfer my data to another computer?<br>
**A**: Install the app in the other computer and overwrite the empty data file it creates with the file that contains the data of your previous Avengers Assemble home folder.

--------------------------------------------------------------------------------------------------------------------

## Known Issues

### Using Multiple Screens

If you move the application to a secondary screen, and later switch to using only the primary screen, the GUI will open off-screen. The remedy is to delete the `preferences.json` file created by the application before running the application again.

### Importing on MacOS

On MacOS computers, due to privacy settings, the application may encounter difficulties accessing and importing CSV files from various locations.
If this issue occurs, transfer the CSV file you want to import to the same folder where the application's JAR file is located, then try again.

--------------------------------------------------------------------------------------------------------------------

## Command Summary

Below is a summary of the commands available in Avengers Assemble. Some examples are included for your convenience.

| Action            | Format, Examples                                                                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Add**           | `add n/NAME p/PHONE_NUMBER e/EMAIL a/ADDRESS [t/TAG]… [m/MATRICULATION_NUMBER] [s/STUDIO] [r/REFLECTION]​` <br><br>• e.g. `add n/James Ho p/22224444 e/jamesho@example.com a/123, Clementi Rd, 1234665 t/friend t/colleague m/A1234567X` |
| **Clear**         | `clear`                                                                                                                                                                                                                                  |
| **Delete**        | `delete INDEX` <br><br>• e.g. `delete 3`                                                                                                                                                                                                 |
| **Edit**          | `edit INDEX [n/NAME] [p/PHONE_NUMBER] [e/EMAIL] [a/ADDRESS] [t/TAG]… [m/MATRICULATION_NUMBER] [s/STUDIO] [r/REFLECTION]​` <br><br>• e.g.`edit 2 n/James Lee e/jameslee@example.com m/A1234567X`                                          |
| **Find**          | `find PREFIX/KEYWORD` <br><br>• e.g. `find n/James`                                                                                                                                                                                      |
| **Copy**          | `copy`                                                                                                                                                                                                                                   |
| **List**          | `list`                                                                                                                                                                                                                                   |
| **Help**          | `help`                                                                                                                                                                                                                                   |
| **Export to CSV** | `export`                                                                                                                                                                                                                                 |
| **Import**        | `import i/FILEPATH` <br><br>• e.g. `import i/C:/Users/alk/Downloads/avengersassemble.csv`                                                                                                                                                |


## Command Format Summary

Some commands require you to include parameters. These parameters are identified by prefixes. Here are a list of valid prefixes and what they each refer to.

<box type="info" seamless>

**Important:** </br>

* Words in `UPPER_CASE` are the parameters to be supplied by the user.<br>
    > e.g. in `add n/NAME`, `NAME` is a parameter which can be used as `add n/John Doe`.

* Prefixes encased with '[ ]' are optional.
    > e.g. `n/NAME [t/TAG]` can be used as `n/John Doe t/friend` or as `n/John Doe`.

* Prefixes with '…' after them can be used multiple times.
    > e.g. `[t/TAG]…​` can be used as ` ` (i.e. 0 times), `t/friend` (i.e 1 time), `t/friend t/family` etc.

* Parameters can be in any order.<br>
    > e.g. if the command specifies `n/NAME p/PHONE_NUMBER`, `p/PHONE_NUMBER n/NAME` is also acceptable.

* Extraneous parameters for commands that do not take in parameters (such as `help` , `list`, `exit`, `copy`, `export` and `clear`) will be ignored.<br>
    > e.g. if the command specifies `help 123`, it will be interpreted as `help`.

</box>

<box type="warning" seamless>

**Caution:** </br>
* If you are using a PDF version of this document, be careful when copying and pasting commands that span multiple lines as space characters surrounding line-breaks may be omitted when copied over to the application.

</box>


| Prefix | What it refers to          | Constraints                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|--------|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| n/     | Name                       | Should only contain alphanumeric characters and spaces.                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| p/     | Phone Number               | Should only contain numbers, and it should be at least 3 digits long.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| e/     | Email                      | **Format:** local-part@domain<br/> **Constraints for local part:**<br/> • Should only contain alphanumeric characters, and the characters `+`, `_`, `.` and `-`<br/> • Should not start with special characters<br/> **Constraints for domain:**<br/> • Made up of domain labels followed by periods<br/> • Must end with a domain label of at least 2 characters long<br/> • Should start and end with alphanumeric characters<br/> • Domain label should consists of alphanumeric characters separated only by hyphens, if any |         
| a/     | Address                    | Can take any values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| i/     | Path of CSV file to import | Should be the absolute file path of the CSV file.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| [m/]   | Matriculation ID           | The first letter must be an uppercase 'A', followed by 7 numbers, and end with an uppercase letter.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| [r/]   | Recitation Group           | The first letter must be an uppercase 'R', followed by any number.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [s/]   | Studio Group               | The first letter must be an uppercase 'S', followed by any number.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| [t/]…  | Tags                       | Should be alphanumeric, and should not contain spaces.                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
