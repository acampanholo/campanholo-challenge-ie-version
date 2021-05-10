# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)


# André Campanholo's Challenge Documentation

## Main Version

The following documentation concerns André Campanholo’s resolution of Intelie’s challenge-chart-plot. There are few inline comments but those were used for development reference only..\
To build the specified application, I used React JS as recommended. It was also a personal choice because React is a great framework to render components on the screen, great for passing data from one component to another and very easy to update information to the user.
The App.js file contains only two components: a simple Header and a component called ChartPlotter. I decided to develop all the other components inside the ChartPlotter component so it would be easier to pass information around from one component to another. The components are: CodeInput, ChartView and Footer. In all components – Header included –, I tried to use all the proper HTML tags for better page indexing.
The CodeInput component receives the data input from the user and sends it back to the ChartPlotter so it can be treated. I imported a component called React-Ace to be my code editor and sent the data to the parent component using a callback function handleOnChange and setting it to the state of the ChartPlotter component. After getting the input value, I created the Footer component containing simply a button with a callback function to handle the click event.
Back in the ChartPlotter component, I defined the handleOnClick function that treats all the data received and sends it to the ChartView component. The function was defined inside the try…catch statement to make sure the application won’t crash in case of invalid data. Instead, the user will receive an error message on the screen. I also created modules to make the process of getting correct information from the object easier. On the handleOnClick function, I converted the string into an object using RegEx with replaceAll() and match() methods and then using the JSON.parse method. I then used the method every() to iterate over the object and extract all the parts of information necessary. I decided to use an Array method over a for loop for personal preference and so it would be easier to handle the already indexed parameters. The every() method was used instead of the forEach() method because the latter does not allow you to easily break the loop. Through the iteration, I used a series of conditionals to be able to access group, select and its values through the object bracket notation. The conditionals also ensure that the limits defined by the start, span and stop values are respected.
The values were treated to build an array correspondent to the data format required by the chart library I used: Google Charts. This treatment considers the order that the data is input by the user, so the second value of any line should be input in the correct order. After the treatment process, which also ensured the begin and end points of the X axis of the chart would respect the span limits, I passed down the data to the ChartView component through props. Inside this component, I defined the plotFinalData() function inside another try…catch statement in order to send the correct array to the component as a property of the chart.  If the user inputs a valid data format but with missing values, another error message will be shown on the screen.

