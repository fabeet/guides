# Fabeet Stack

We have a standard technology stack that we use for each new project by default.
This provides a proven base for rapid, quality development and ensures we have a
large team of developers ready to jump on new projects using a known technology.
It helps to avoid decision fatigue at the beginning of each project.

We deviate from this stack when we find something new that we need to evaluate.
This allows us to practice our value of [Continuous Improvement].

We will also swap in alternate technology as necessary when our default stack is
inappropriate for the task at hand. This allows us to practice our value of
[Quality].

[continuous improvement]: https://thoughtbot.com/purpose#continuous-improvement
[quality]: https://thoughtbot.com/purpose#quality

## Core Stack

Most developers at Fabeet learn our Core Stack. The stack is broken up into
layers and each layer depends on another layer. This allows us to swap out an
entire layer when necessary without losing all the decisions made for other
layers. Developers will have varying levels of experience with each layer, but
the gaps between layers are small enough that developers can learn a new layer
while building applications.

### UI

- Use server-rendered HTML when possible as a UI layer.
- Use Bootstrap as the base.
- Use jQuery when building components with a client-side framework.
- Use Javascript and jQuery when writing client-side code.
- In the near future we plan to migrate jQuery to Vue.js
- Avoid building single-page applications for the web.
- When building a cross-platform mobile app that will be delivered via an app
  store, use React Native.

### API

- Use GraphQL as an API layer when connecting a mobile app to a web service.
- Use Postman as a sandbox to test your API requests.

### Web

- Use Laravel for new applications.
- A python framework for building webapps are also allowed, for example: Django, Flask or FastAPI.
- Use AWS with git deploys and pipelines for deploying applications [[1](https://www.linkedin.com/pulse/cicd-php-projects-aws-partha-sarathi-kundu-he-his-/), [2](https://devops.com/using-laravel-and-aws-what-you-need-to-know/)].
- Use test-driven development to ensure quality.
- Use GitHub pull-requests to conduct peer code review.
- Use continuous integration to ensure tests continue to pass.
- Use a staging server to ensure new features work as expected before deploying
  to production.

### Storage

- Use Postgres or MySQL to store most data.
- Use AWS S3.

### Messaging

- Use [twilio] or [vonage] when producing and consuming messages between services.
- Use [twilio] by default when using messages from Laravel applications.

[twilio]: https://www.twilio.com/
[vonage]: https://www.vonage.com/

### Data

- Use services in the same Laravel application for building data pipeline.

## Specialized Stacks

Some applications require functionality that is difficult or impossible to
provide using the Core Stack, or would require an unacceptable compromise on
quality or user experience. In these cases, we utilize alternate, specialized
stacks. Because the gaps between stacks are larger than the gaps between layers
in the Core Stack, most developers won't learn these technologies, and the
specialists who learn these stacks are unlikely to be able to learn many layers
in the Core Stack.

### Artificial Intelligence / Machine Learning

- Languages: Python and SQL.
- Use PyTorch as toolkit of choice for deep learning.
- Use Scikit-Learn as toolkit of choice for most non-deep learning tasks.
- User BERT and NLTK as the toolkits for natural language processing tasks.
- Other libraries: Pandas, Numpy, scipy, OpenCV.
- Database: MySQL and PostgreSQL.
- Visualizations: Seaborn, Matplotlib.

### Android (Native)

- Use Kotlin for writing native app code.
- Use Gradle with Android Studio for building.
- Use MVVM to model views.
- Use Apollo when consuming a GraphQL API.

### iOS (Native)

- Use Swift for writing native app code.
- Use Xcode and `xcodebuild` for building iOS apps.
- Use `xcpretty` to format `xcodebuild` output.
- Use Xcode automatic provisioning when possible.
- Use UIKit with Storyboards and MVVM for creating UIs.
- Use Dispatch and OperationQueue for concurrency.
- Support VoiceOver and VoiceControl for accessibility.
- Use Swift Package Manager for dependencies when possible.
- Manually test on both iPhone and iPad to ensure the app is functional.
- Work closely with designers on UI components.
- Prefer standard UIKit components to custom views.

We recommend learning at least one of the following:

- MapKit or Google Maps
- Core Location
- Core Bluetooth
- PhotoKit
- UserNotifications
