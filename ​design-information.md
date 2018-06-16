# Design Information


1. A user will be able to choose to log in as a specific ​player ​or create a new player when starting the application. For simplicity, any authentication is optional, and you may assume there is a single system running the application.

* The class *User* has been created with operations "login()" and "CreateNewPlayer()" in order to realize the function of log in and create new players. The *Player* class with attributes of "firstName", "lastName", "userName", "email" and severl operations is designed. In detail, "checkUserNameUniqle()" will check if the username input is uniqle, "createCryptogram()" will allow the player to create new cryptograms, "viewUnsolvedCryptogramList()" will display the full list of unsolved cryptograms, "solveCryptogram()" will allow the player to solve the puzzle with the help of association class *SolvingCryptogram*, "viewCompletedCryptogramList()" will allow the user to see the cryptograms that have been completed, no matter success or not, and finally "viewCryptogramStatistics()" provides a statistical view about the cryptograms.
-----

2. The application will allow ​players ​to (1) create a cryptogram, (2) choose a cryptogram to solve, (3) solve cryptograms, (4) view their ​list of completed cryptograms​, and (5) view the ​list of cryptogram statistics​.

* (1) The player is able to create a cryptogram with the *Player* class's operation "createCryptogram"; When an cryptogram is created, there will be attributes "puzzleName", "solution", "encodedPhrase", "maximumNumberAllowed", and "dateCreated";
* (2) The player is able to view the list of unsolved cryptograms with the operation "viewUnsolvedCryptogramList()" in the *Player* class; and then the player can choose a specific cryptogram with the operation of "viewCryptogram()";
* (3) The operation "solveCryptogram()" in the *Player* class and the association class *SolvingCryptogram* was designed to fulfill the function of solving cryptograms;
* (4) The operation "viewCompletedCryptogramList()" in the *Player* class will allow the player to take a look at the completed cryptograms;
* (5) The operation "viewCryptogramStatistics()" in the *Player* class allows the player to have a statistical view about the cryptograms.
-----

3. A cryptogram will have an encoded phrase (encoded with a simple substitution cipher), a solution, and a maximum number of allowed solution attempts. A cryptogram will only encode alphabetic characters, but may include other characters (such as punctuation or white space) in the puzzle, which will remain unaltered. Capitalization is preserved when encoded.

* The attributes "encodedPhrase", "solution", "maximumNumberAllowed" in the *Cryptogram* class are designed to fulfill the requirements. There will be statements examing whether the character is alphabetic or other character. The capitalization will be examined as well.
-----

4. To add a player, the user will enter the following player information:
a. A first name
b. A last name
c. A unique username
d. An email

* The attributes "firstName", "lastName", "userName", "email" in the *Player* class will be created, and the operation "checkUsernameUniqle()" will be used to check whether the "userName" is uniqle.
-----

5. To add a new cryptogram, a player will:
a. Enter a unique cryptogram puzzle name.
b. Enter a solution (unencoded) phrase.
c. Choose different letters to pair with every letter present in the phrase.
d. View the encoded phrase.
e. Enter a maximum number of allowed solution attempts.
f. Edit any of the above steps as necessary.
g. Save the complete cryptogram.
h. View a confirmation that the name assigned to the cryptogram is unique and
return to the main menu.

The attributes "puzzleName", "solution" in the *Cryptogram* class are designed to fulfill requirements a and b. The letters to pair with every letter present will be stored in the attribute "letterPairs". The player can view the encoded phrase with operation "viewEncodedPhrase()" in the *Cryptogram* class. The attribute "maximumNumberAllowed" is used to store the input of maximum number of allowed solution attempts. The operation "editCryptogram()" will allow the player to make adjustment to any of the inputs. The operation "saveCryptogram()" allows the player to save the cryptogram. The operation "viewConfirmation()" is designed for the requirement of determining whether the cryptogram name is unique. Operation "returnToMain()" leads the player back to the main menu.
-----

6. To choose and solve a cryptogram, a player will:
a. Choose a cryptogram from a list of all unsolved cryptograms.
b. View the chosen cryptogram and number of incorrect solution submissions
(starting at 0 for a cryptogram that has not previously been attempted).
c. Match the replacement and encrypted letters together, and view the resulting
potential solution.
d. When all letters in the puzzle are replaced and they are satisfied with the
potential solution, submit their answer.
e. Get a result indicating that the solution was successful, or incrementing the
number of incorrect solution submissions if it was unsuccessful.
f. At any point, the player may return to the list of unsolved cryptograms to try
another.
g. If the number of incorrect solution attempts increases to the maximum allowed
number of solution attempts, they will get a result that the cryptogram game was lost, and this cryptogram will be moved to the completed list.

* The association class *SolvingCryptogram* is designed to let the player solve the cryptogram. The player is able to view unsolved crytpogram through the operation "viewUnsolvedCryptogram()" in the *Player* class. Then the player can choose and view the cryptogram via the operation "viewCryptogram()" in the *Player* class. "viewNumberIncorrectAttempt()" allows the player to see the number of incorrect solution submissions. The input letter pairs will be stored in the attribute "letterPairs". The operation "matchTogether()" will do the trick and match the replacement and encrypted letters. "viewPotentialSolution()" will show the potential result generated after the match. When the player is satisfied, the operation "submitAnswer()" will be able to submit the solution. If the solution matches the solution in the *Cryptogram* class, the operation "indicateSuccess()" will let the player know it is successful. Otherwise, the operation "incrementNumberIncorrect()" will increase the number of incorrect attempt by 1. "returnToUnsolvedList()" allows the player to go back to the unsolved list whenever the player wants to do so. "indicateLoss()" will take effect when the number of incorrect solution attempts increases to the maximum allowed number of solution attempts. Then the cryptogram will be moved to the completed cryptogram list.
-----

7. The list of unsolved cryptograms will show the cryptogram’s name and the number of incorrect solution attempts (if any) for that player.

* The player will be displayed with a list of unsolved cryptograms with the operation "viewCryptogram()" in the *Player* class. The cryptogram's name was saved in the *Cryptogram* class with "puzzleName" attribute and the operation "showCryptogramName()" in the *UnsolvedCryptogramList* class will be able to display the names. The number of incorrect solution attempts is saved in the *SolvingCryptogram* association class with the attribute "numberIncorrectAttempt" and the operation "showIncorrectAttempts()" in the *UnsolvedCryptogramList* class will show the number of incorrect attempts.
-----

8. The list of completed cryptograms for that player will show the cryptogram’s name, whether it was successfully solved, and the date it was completed.

* The player is able to view the completed cryptograms with the operation "viewCompletedCryptogramList()" in the *Player* class. The cryptogram's name is stored in the attribute "puzzleName" and the operation "showCryptogramName()" in the *CompletedCryptogramList* class will be able to display the names. Whether the cryptogram is success is stored in the attribute "ifSuccess" in *SolvingCryptogram* association class and the operation "showIfSuccess()" in the *CompletedCryptogramList* class will be able to display the names. The date completed is stored in the attribute "dateCompleted" in the *SolvingCryptogram* association class as well and the operation "showCompletedDate()" in the *CompletedCryptogramList* class will be able to display the completion date.
-----

9. The list of cryptogram statistics will display a list of cryptograms in order of creation. Choosing each cryptogram will display the date it was created, the number of players who have solved the cryptogram, and the username of the first three players to solve the cryptogram.

* The cryptogram statistics will be shown with the operation "viewCryptogramStatistics()" in the *Player* class. Specifically, the operation "showAllCryptograms()" will display all of the cryptograms. The operation "sortCryptograms()" in the *CryptogramStatistics* class will sort them according to the creation time based on the attribute "dateCreated" in the *Cryptogram* class. The date will be displayed by operation "showDateCreated()" in the *CryptogramStatistics* class. The operation "showNumberPlayersSolved()" is designed to fulfill the requirement of showing the number of players solved the cryptogram. Lastly, "showFirstThreePlayersSolved()" will display the first three player's username.
-----

10. The User Interface (UI) must be intuitive and responsive.

* The User Interface will be carefully designed to let the user love our software. All of the input frame and buttons will be easy to operate with.
-----

11. The performance of the game should be such that players does not experience any considerable lag between their actions and the response of the game.

* The software will be designed as smooth and light as possible. No redundant information or function will be introduced to make sure the user will have a wonderful experience about our software. It will be ensured that right after the input or click of the user, the software will make the corresponding reactions.
-----

