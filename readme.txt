To run the website on your computer,create a new react application and making sure that all the below mentioned dependencies are present.
"dependencies": {
    "@testing-library/jest-dom": "^5.16.5",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "antd": "^5.4.3",
    "bootstrap": "^5.2.3",
    "firebase": "^9.20.0",
    "firestore": "^1.1.6",
    "react": "^18.2.0",
    "react-bootstrap": "^2.7.4",
    "react-dom": "^18.2.0",
    "react-hook-form": "^7.43.9",
    "react-icons": "^4.8.0",
    "react-router-dom": "^6.10.0",
    "react-scripts": "5.0.1",
    "reactjs-popup": "^2.0.5",
    "web-vitals": "^2.1.4"
  },

1.Authentication -
       We used firebase Auth to provide authentication to our users. They need to give their email and set their password at the time of signup and the corresponding details will be stored in firebase Auth. When the user tries to login , it searches for the email provided in the firebase and checks if the password matches with it. We made use of some inbuilt functions signInWithEmailAndPassword(auth, email, password) to make the users sign in.

2.Firestore-
        We used Firebase firestore as our database to store information regarding the rides initiated by the drivers and the passengers accepted by the driver. We made three collections in the database , one for storing the ride information which was initiated by the driver like fare per person , starting and ending locations, car model , whose id is set as the email id of the driver who initiated it, one for storing the details of details of the passengers who are willing to join the ride initiated by the driver, the email id of the driver is set as the id for this . and other for the list of members who are already accepted by the driver whose is the email id of the driver. So we are creating three documents in the firebase at the time of creation of the ride by the driver with id as his email id . which stores ride details, willing to join his ride and already joined his ride. We used the inbuilt function provided by the firebase like setDoc,Doc, getDoc, updateDoc etc.,
 
3 .Driverinput-
    	 Driver has to enter the ride details such as time of start, way number (assigned in the map) corresponding to the given map from where to where they wanted to travel, fare per person. These are stored in the firebase under the “rides document”. While uploading the document in the firestore it checks whether the user is signed in or not and then it checks whether the provided details are valid or not and then the document is added to the firebase which will be displayed to the passenger when the locations entered by the passenger are the same . 

4. Maps input-
            We are having fixed number of locations on the map which are having buttons at that place and there are fixed number of paths that contain a set of locations. Driver can travel from one location to the other location contained in the same path . When the passenger selects the starting and ending location using the map contained in the same path, the rides which are travelling in the same path are displayed to the passenger including their details.

5. Navbar-
          For passenger , the navbar shows join new ride and my ride . My ride contains the list of rides for which he has already registered for. For driver, the navbar contains new ride where he can initiate a new ride and my ride where he can find the details of the ride initiated by him. It also contains the sign out button on clicking on that he can sign out.
 
5. Join in Ride-
           When the passenger selects the starting and ending locations on the map, the rides in which the driver is travelling in the same path are displayed to the passenger and there is join button for each of the rides. If the number of passengers already registered are less than 4 then it sends  notification to the driver that the particular user wants to join his ride. If he accepts for that, then that user will be added to the joined list of the driver. 

CHOOSING LOCATIONS: 
● After verifying the user, user is directed to the home page,where he/she can choose the pick up and destination locations. 
● User can choose locations using maps as well as enter manually.
 ● After entering the location, user is directed to the rides page. 

CHOOSING RIDE: 
● In the rides page,suitable rides for the user are displayed. 
● The user can choose a ride and send a request to the driver.If the user does not find a suitable ride ,he/she can initiate a ride.
 ● Also,if the driver has not accepted the request then a “request declined” message will be popped up.In this case,the user can go for another ride.

CANCEL RIDE: 
● If the user wants to cancel the ride,he/she can simply go to the rides page and click on the cancel option.If the user has not chosen any ride yet then “You have not selected a ride” message will be popped up.Otherwise,the ride will get canceled.

