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

git remote add origin https://github.com/DJTechnologies/nucampweek3.git

compon.js

import React, { Component } from "react";
import {
Card,
CardImg,
CardText,
CardBody,
CardTitle,
Breadcrumb,
BreadcrumbItem,
} from "reactstrap";
import { Link } from "react-router-dom";

class CampsiteInfo extends Component {
renderCampsite(campsite) {
return (

<div className="col-md-5 m-1">
<Card>
<CardImg top src={campsite.image} alt={campsite.name} />
<CardBody>
<CardTitle>{campsite.name}</CardTitle>
<CardText>{campsite.description}</CardText>
</CardBody>
</Card>
</div>
);
}

renderComments(comments) {
if (comments) {
return (

<div className="col-md-5 m-1">
<h4>Comments</h4>
{comments.map((comments) => (
<div className="p-1" key={comments.id}>
{comments.text}
<br></br>
-- {comments.author},{" "}
{new Intl.DateTimeFormat("en-US", {
year: "numeric",
month: "short",
day: "2-digit",
}).format(new Date(Date.parse(comments.date)))}
</div>
))}
</div>
);
} else {
return <div></div>;
}
}

render() {
if (this.props.campsite) {
return (

<div className="row">
{this.renderCampsite(this.props.campsite)}
{this.renderComments(this.props.comments)}
</div>
);
} else {
return <div></div>;
}
}
}

export default CampsiteInfo;

about
import React from "react";
import {
Breadcrumb,
BreadcrumbItem,
Card,
CardBody,
CardHeader,
Media,
} from "reactstrap";
import { Link } from "react-router-dom";

function About(props) {
const partners = props.partners.map((partner) => {
return <h5>{partner.name}</h5>;
});

return (

<div className="container">
<div className="row">
<div className="col">
<Breadcrumb>
<BreadcrumbItem>
<Link to="/home">Home</Link>
</BreadcrumbItem>
<BreadcrumbItem active>About Us</BreadcrumbItem>
</Breadcrumb>
<h2>About Us</h2>
<hr />
</div>
</div>
<div className="row row-content">
<div className="col-sm-6">
<h3>Our Mission</h3>
<p>
We present a curated database of the best campsites in the vast
woods and backcountry of the World Wide Web Wilderness. We increase
access to adventure for the public while promoting safe and
respectful use of resources. The expert wilderness trekkers on our
staff personally verify each campsite to make sure that they are up
to our standards. We also present a platform for campers to share
reviews on campsites they have visited with each other.
</p>
</div>
<div className="col-sm-6">
<Card>
<CardHeader className="bg-primary text-white">
<h3>Facts At a Glance</h3>
</CardHeader>
<CardBody>
<dl className="row">
<dt className="col-6">Founded</dt>
<dd className="col-6">February 3, 2016</dd>
<dt className="col-6">No. of Campsites in 2019</dt>
<dd className="col-6">563</dd>
<dt className="col-6">No. of Reviews in 2019</dt>
<dd className="col-6">4388</dd>
<dt className="col-6">Employees</dt>
<dd className="col-6">42</dd>
</dl>
</CardBody>
</Card>
</div>
<div className="col">
<Card className="bg-light mt-3">
<CardBody>
<blockquote className="blockquote">
<p className="mb-0">
I will not follow where the path may lead, but I will go where
there is no path, and I will leave a trail.
</p>
<footer className="blockquote-footer">
Muriel Strode,{" "}
<cite title="Source Title">
"Wind-Wafted Wild Flowers" - The Open Court, 1903
</cite>
</footer>
</blockquote>
</CardBody>
</Card>
</div>
</div>
<div className="row row-content">
<div className="col-12">
<h3>Community Partners</h3>
</div>
<div className="col mt-4">
<Media list>{partners}</Media>
</div>
</div>
</div>
);
}

export default About;

main
import React, { Component } from "react";

import Directory from "./DirectoryComponent";
import CampsiteInfo from "./CampsiteInfoComponent";
import { CAMPSITES } from "../shared/campsites";
import Header from "./HeaderComponent";
import Footer from "./FooterComponent";
import Home from "./HomeComponent";
import Contact from "./ContactComponent";
import { Switch, Route, Redirect } from "react-router-dom";
import { COMMENTS } from "../shared/comments";
import { PARTNERS } from "../shared/partners";
import { PROMOTIONS } from "../shared/promotions";
// added today
import About from "./AboutComponents";

class Main extends Component {
constructor(props) {
super(props);
this.state = {
campsites: CAMPSITES,
comments: COMMENTS,
partners: PARTNERS,
promotions: PROMOTIONS,
};
}

render() {
const HomePage = () => {
return (
<Home
campsite={
this.state.campsites.filter((campsite) => campsite.featured)[0]
}
promotion={
this.state.promotions.filter((promotion) => promotion.featured)[0]
}
partner={this.state.partners.filter((partner) => partner.featured)[0]}
/>
);
};

    const CampsiteWithId = ({ match }) => {
      return (
        <CampsiteInfo
          campsite={
            this.state.campsites.filter(
              (campsite) => campsite.id === +match.params.campsiteId
            )[0]
          }
          comments={this.state.comments.filter(
            (comment) => comment.campsiteId === +match.params.campsiteId
          )}
        />
      );
    };

    return (
      <div>
        <Header />
        <Switch>
          <Route path="/home" component={HomePage} />
          <Route
            exact
            path="/directory"
            render={() => <Directory campsites={this.state.campsites} />}
          />
          <Route path="/directory/:campsiteId" component={CampsiteWithId} />
          <Route exact path="/contactus" component={Contact} />

          <Redirect to="/home" />
        </Switch>

        <Footer />
      </div>
    );

}
}

export default Main;
