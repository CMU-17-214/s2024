# Homework 5: Concurrency

In this assignment you will work with concurrency in a Node backend and will modify a React frontend. You will get experience with writing asynchronous code, with error handling, and with handling state in React.

## Starter code

Find the starter code with the GitHub Classroom link on Canvas.

You will work on a semi-completed program *SmilingFaces* to analyze faces in Wikipedia pages -- for example are more people smiling in pictures of the Carnegie Mellon Wikipedia page or in the University of Pittsburgh wikipedia page? In the web application, you can enter a *topic* for which a Wikipedia page exists and the program will identify all images in the page and determine with an ML model whether the picture contains smiling faces. It can also collect the pictures from other Wikipedia pages linked heavily from the target page ("include top neighbor topics").

The starter code already handles all the communication with Wikipedia and the Google Cloud Vision API, but the backend code is currently written synchronously (which is actually quite difficult to do and very unusual for Node code). As a consequence the backend can only respond to a single request at a time and it is very slow. The provided implementation is also bad at error handling.

The code consists of two related projects: The backend *express* implementation in the root directory and the frontend *React* implementation in directory `frontend`.  Compile and run the code as follows:

* First, build the frontend
  * run `npm install`  in the `frontend/` directory. (Note: deprecation and security vulnerability warnings here are expected)
  * `npm run build` in `frontend/` to build the frontend, which will result in static pages in `frontend/build/`
* Second, build and run the backend
  * run `npm install` in the root directory
  * `npm run compile` builds the backend, resulting in Javascript code in `dist/` as usual
  * Make sure that you are signed into the Google Cloud API using `gcloud` (same as Lab 8)
  * `npm run start` runs the server which you can then access at `http://localhost:8080`

The backend serves the frontend code in the root of the web server but also provides API endpoints for starting a job (`POST /job`) and for getting results of a job (`GET /job/:id`) that both communicate in JSON format (using the [Long Running Operation with Polling Pattern](http://restalk-patterns.org/long-running-operation-polling.html)). The frontend will make requests to the APIs to update the state within the page. If a job is not completed on the first request, it will check every second for updates.

In the user interface in the web browser you can enter a topic and start the analysis. Note that the response will take a very long time if you analyze any nontrivial pages. Analyzing the topic "Carnegie Mellon University" gathers and analyzes 30 images without neighboring pages (and many more with neighbors), which easily takes 30 seconds to respond. A good test page might be "David Tepper" which has only a single image and takes about 2 seconds to analyze.

## Tasks

**Concurrency in the backend.** Rewrite the backend to perform computations concurrently. We have the following requirements of the final implementation:

* The server makes requests to Wikipedia and the Google Cloud API concurrently, speeding up responses significantly.
* The server can answer multiple requests concurrently (i.e., multiple calls to `/job` and `/job/:id`).
* The server reports an error when more than 5 jobs are processed concurrently asking users to try again later. Reject additional requests with HTTP error code 503.
* The server never makes more than 5 concurrent requests to Wikipedia and never more than 5 concurrent requests to the Google Cloud API in order to not overload those servers (this limit is shared by all jobs).
* If multiple topics are analyzed, the server does not wait until all images are collected from all topics, but starts analyzing images as soon as the images from each topic are identified.

**Error handling.** Make the implementation robust to errors. Specifically we expect you to handle the following kind of errors:

* When connections to Wikipedia or the Google Cloud API fail (error, timeout, or invalid results) retry two more times after a short wait of one second.
* When connections to Wikipedia or the Google Cloud API fail and cannot be recovered or any other computations fail, report an error message to the frontend gracefully. Your server should still be able to handle 5 concurrent jobs and up to 5 concurrent backend requests afterward.
* The backend validates inputs received from the frontend. Reject empty and invalid inputs with HTTP error code 400.

**Frontend improvements.** Improve the React frontend with some minor extensions

* Allow incremental loading in the frontend, by polling regularly for updates from the backend. (This should work out of the box if the backend responds correctly)
* Show a progress bar while data is loaded.
* Show errors from the backend in the frontend, ideally with meaningful error messages.

**What not to change:** We plan to automate some testing of your code, as such, do NOT change the `Connections` interface and the signature of the `smilingFacesBackend` function. Also do not change the protocol between the backend and frontend (i.e., do not change the API endpoint addresses and the interfaces in `jobdata.ts`). If we cannot grade your submission because you change any of these, we will assign zero points to that specific rubric item. Make all external calls through the APIs in `Connections` and do not make web calls with any other API. You may, and probably should, develop your own abstractions on top of the functions in `Connections`.

## Submitting your work

As usual, submit all your changes to GitHub. Once you have pushed your final code, submit a link to your final commit on Canvas. A link will look like `https://github.com/CMU-17-214/<reponame>/commit/<commitid>`. You can get to this link easily when you click on the last commit (above the list of files) in the GitHub web interface.

## Evaluation

This assignment is worth 100 points. We will grade the assignment with the rubric below. Submissions that do not provide a link in the expected format can not be graded and will not receive credit.

Concurrency:

* [ ] [10 points] The backend code makes use of concurrency to speed up computations for getting Wikipedia requests
* [ ] [10 points] The backend code makes use of concurrency to speed up computations for analyzing images with the Google Cloud API.
* [ ] [10 points] The backend code can process multiple jobs concurrently.
* [ ] [10 points] The backend successfully completes computations and provides the results through the API.
* [ ] [5 points] The backend rejects additional new jobs when processing 5 jobs concurrently with HTTP error code 503
* [ ] [5 points] The backend correctly limits concurrency to at most 5 concurrent requests each to Wikipedia and Google.
* [ ] [5 points] The backend can process images after images are identified from a topic, independent of other topics also to be analyzed.

Error handling:

* [ ] [5 points] The backend implements a retry mechanism for failed Wikipedia and Google connections, that makes two more attempts with a one second wait after each failed attempt.
* [ ] [5 points] The backend recovers gracefully from failed Wikipedia and Google connections, reporting an error message to the client. Errors do not reduce the ability to perform work concurrently.

Frontend:

* [ ] [5 points] The frontend supports incremental loading of results
* [ ] [5 points] The frontend shows a progress bar while results are loaded
* [ ] [5 points] The frontend shows errors from the backend if computations fail

Others:

* [ ] [10 points] The frontend and backend code compiles on GitHub Actions.
* [ ] [5 points] Commit messages are reasonably cohesive and have reasonable messages.
* [ ] [5 points] The code is free of severe readability and style issues.

## Appendix: Hints and Tooling Tips

**How to start:** The code is functional as provided. Identify where the *sync* functions from `Connections` are called and understand how they are used. Incrementally turn synchronous functions in asynchronous ones by changing return type `T` to `Promise<T>` and updating the implementation of the function and its call sides accordingly.

It is difficult to make only local changes as incremental refactorings. It might be easier to change the entire WikipediaAPI or VisionAPI class at once. If necessary, comment out the vision API steps first and just get images from topics with and without neighboring topics. It might be useful to write simple tests for the calls to the Wikipedia API that can run outside the backend, e.g., with jest or with a simple main function just calling `newWikipediaAPI(new DefaultConnection()).getImageLinksFromTopic("David Tepper")`.

**Implementation suggestions:** We recommend to use promises or async/await. It might be a good starting point to turn the provided connection functions with callbacks into promises. Beyond that you might find `Promise.all` useful.

You can consider streams (`ReadableStream` of the Web Streams) for some of the work, but it is not required.

The homework changes can all be fully implementing with plain Node code. Consider using the Proxy pattern to modularize error handling. If you like, you can use external libraries, such as `p-limit` or one of the many retry libraries.

The library `express` works very similar to the NanoHTTP library in Java you have seen before. You will likely not need to modify the express code itself. The React code to handle multiple jobs and incremental updates is not trivial, but also not overly complex -- you will not need to substantially modify this.

The execution order of concurrent code may not always be intuitive. Consider using a debugger or using print statements in the code to follow the execution.

**Testing suggestions:** Writing tests may be useful, but is not required in this assignment. There are good opportunities for testing with stubs in the backend; the backend code is written in a way to make this testing easy by avoiding global functions. We do not suggest to test frontend code.

A basic testing infrastructure is already setup in directory `tests/`, but tests are commented out. The example tests use stubs, but you can also run tests against Wikipedia and Google Cloud by just using the `DefaultConnection` class. Of course you can also test parts of your implementation without starting express, for example by writing tests for the functions in `wikipediaapi.ts`.

While you are not required to automate tests, we will use tests in the style of the provided examples for grading.

**Tooling suggestions:** If you want to send requests to the backend without running the frontend, you can send requests on the command line, such as

```bash
curl -X POST -H "Content-Type: application/json" -d '{"name": "David Tepper", "withNeighbors": false}' http://localhost:8080/job
```

With `npx tsc --watch` you can keep the TypeScript compiler running in a terminal and it will automatically compile changes whenever you safe a file. In a second terminal,  `npx nodemon .` it will restart your application (the backend) after every change, that is, whenever the compiler has produced a new version. The test runner `jest` watches changes by default.

For the frontend `npx react-scripts start` provides a development environment that refreshes automatically whenever any React files are changed. This unfortunately does not connect to the backend automatically, but can be used for pure frontend development. You can test frontend code during development if you set the initial state (`const initialJobs: JobInfo[]`) to something more interesting that contains actual results, e.g., those received with the curl command above.
