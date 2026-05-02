---
title: Ways to optimise performance in React applications
slug: ways-to-optimise-performance-in-react-applications
createdAt: '2026-05-02T15:38:45.423Z'
updatedAt: '2026-05-02T15:42:12.441Z'
metadata:
  title: Ways to optimise performance in React applications
  description: ''
  heroImage: 'https://imgur.com/RzLeI9S.png'
  draft: true
  publishedAt: '2024-05-30T15:38:00.000Z'
description: ''
heroImage: 'https://imgur.com/RzLeI9S.png'
draft: false
publishedAt: '2024-05-30T10:08:00.000Z'
---
Performance optimization is crucial in web development. Users prefer fast-loading as they get instant gratification. Achieving optimal performance is complex, we need to understand Core web vitals and how to read & improve them, API consumptions, using of react profiler to identify component bottlenecks, utilize memoization techniques to improve load times and responsiveness, enhancing the user experience.

----------

## How to start?

  
Generally, I would start by looking at the current metrics of the app.

-   Utilize browser developer tools such as Chrome DevTools or Firefox Developer Tools to measure performance metrics.
    -   Use performance monitoring tools like Lighthouse locally to get a basic understanding of web vitals
    -   We need to look at the network waterfall model, identify which APIs are taking a lot of time, and flag them up for further evaluation. Mark synchronous and asynchronous API calls and their dependency on UI rendering i.e. how it is impacting the LCP
        
        source: [https://web.dev/articles/lcp](https://web.dev/articles/lcp)
        

Below are the steps we can consider for app pref improvements.

## Optimizing API Calls

Unnecessary API calls can block rendering, degrade application performance, especially synchronous ones, and delay UI updates. For example, you are calling three APIs from your landing page e.g. A, B, and C but for initial rendering, you only need data from A. So It’s better to skip the calling of B and C. Another good example would be if you require data from all the APIs i.e. A, B, and C but you are calling synchronously and there is no need for synchronous calls then it’s better to fetch all of them asynchronously.

Developers should consider this step while working on the apps

### Solution

Implement loading states for components to prevent blocking rendering while awaiting API responses. Use asynchronous data fetching techniques to fetch data after the initial render, ensuring a responsive user interface.

### Benefits

-   **Improved Rendering**: By not blocking rendering for API calls, the application remains responsive and provides a better user experience.
    
-   **Faster Load Times**: Asynchronous data fetching reduces initial load times, allowing users to interact with the application sooner.
    
-   **Reduced Server Load**: Minimizing unnecessary API calls reduces server load and improves scalability.
    

## Code Splitting and Lazy Loading

As a dev, we all know about Code splitting in React, a technique used to split a large JavaScript bundle into smaller, manageable chunks. It helps improve performance by loading only the necessary code for a specific part of an application rather than loading the entire bundle upfront. When you develop a new React application, all your JavaScript code is typically bundled together into a single file. This file contains all the components, libraries, and other code required for your application to function.

But as your application grows, the bundle size can become quite large, resulting in slow initial load times for your users. This is happening in our Tekion web apps also.

Code splitting allows you to divide a single bundle into multiple chunks, which can be loaded selectively based on the current needs of your application. Instead of downloading the entire bundle upfront, only the necessary code is fetched and executed when a user visits a particular page or triggers a specific action.

### Solution

Implement code splitting to divide the application code into smaller, more manageable chunks. Utilize lazy loading to load components dynamically only when they are needed, reducing the initial bundle size and improving load times.

### Benefits

-   **Faster Initial Load**: Smaller bundle sizes result in faster initial load times, improving the perceived performance of the application. The speed at which a website loads and displays content becomes faster.
    
-   **Improved Resource Utilization**: Lazy loading ensures that only essential components are loaded initially, reducing unnecessary resource consumption.
    
-   **Enhanced Scalability**: Code splitting allows for better scalability by enabling incremental loading of additional features as the application grows.
    
-   The interaction time improves.
    
-   The percentage of users who abandon the web page without interacting with it decreases
    

## Optimizing Static Assets

Including static assets such as images and SVGs directly in the codebase can increase bundle size and affect load times, especially for large files.

### Solution

Move static assets to a separate storage solution such as an S3 bucket or a CDN. Replace direct references in the codebase with URLs pointing to the external storage location.

### Benefits

-   **Reduced Bundle Size**: Removing static assets from the codebase reduces the overall bundle size, leading to faster load times and improved performance.
    
-   **Efficient Caching**: CDNs and storage solutions often provide efficient caching mechanisms, further enhancing load times and reducing server load.
    
-   **Simplified Deployment**: Separating static assets from the codebase simplifies deployment and version control, making managing and updating assets independently easier.
    

## Lazy Loading Images in React

When a React application contains many images, the DOM will render all images altogether before displaying the user screen, leading to performance degradation.

Another point, it also impacts Cumulative Layout Shift (CLS), a user-centric metric for measuring visual stability, as it quantifies how often users encounter unexpected layout shifts. A low CLS ensures a delightful browsing experience by minimizing disruptive changes to the page layout.

source: [https://web.dev/articles/cls](https://web.dev/articles/cls)

### Solution

1.  Implement lazy loading for images, which waits until the image appears on the user screen before rendering it, preventing unnecessary DOM node creation and improving performance.
    
2.  To avoid layout shifts, we can shimmers or give exact space in the current DOM for future rendering of images/contents.
    

Shimmer loading, also known as lazy load, is an animation trick that shows users that a page is still loading while data is being fetched. Shimmers are placeholder shapes that appear where data will eventually be displayed. They are often used when data is being fetched from a remote server or a local database is being queried.

### Functional Components & Component Interaction

The subtle way of optimizing the performance of React applications is by using functional components. Though it sounds cliché, it is the most straightforward and proven tactic to build efficient and performant React applications speedily. React Dev community suggests keeping your components small because smaller components are easier to read, test, maintain, and reuse.

Some advantages of using React components:

### Benefits

-   Require less code
    
-   Easy to understand
    
-   Easy to test
    
-   Flexibility to extract smaller components
    
-   Improved interactability
    

## React Redux Optimization Tips

A well-known flaw faced by Yahoo is a classic example to consider when React apps are built with Redux. Indeed, the combination is deadly and enables complex situations to structurize, but when you use Redux, your React app rerenders and slows down your performance.

There are two ways how you can overcome this challenge with React Redux applications. The first one is using the RESELECT library when the higher-order components in your React app are allocated for rendering operations. Yahoo immensely benefited by using this library.

Another method to optimize React Redux app performance is by using Immutable.js. The performance of an immutable list was much more (up to 4 times) than a mutable list. When you use mutable data structures in a Redux app, the Redux state tree consumes a lot of memory for copying data, hence hampering the app’s performance.

Using an immutable data structure will not update the original data and instead generate a new version of the updated data structure whenever requested. This technique improves the React performance drastically.

### Solution

Use libraries like Reselect and Immutable.js to improve performance and memory management.

### Benefits

-   Enhanced performance
    
-   Improved memory management
    
-   Reduced rerenders
    

## React Memoization Techniques

We are all aware of improtance of memoization techniques, which reduces component rerenders. Please relook at the usage of useCallback, useMemo, memo on your component to reduce unnecessary rerenders.  
external doc - [https://www.freecodecamp.org/news/react-performance-optimization-techniques/#usetransition-hook](https://www.freecodecamp.org/news/react-performance-optimization-techniques/#usetransition-hook)

## Trim JavaScript Bundles (additional setup if not done on your repo)

Redundant and unnecessary code in JavaScript bundles can increase bundle size and affect application performance. Here bundlers like Webpack can use _tree_-_shaking_ techniques to remove unreachable code (also known as dead code) from a bundle.

### Solution

Trim JavaScript bundles by removing duplicates and unnecessary code, resulting in smaller bundle sizes and improved performance.

----------

I tried to cover various aspects of performance optimization in React applications. These can be applied in any react-based UI code bases, ranging from API calls to static assets, with solutions and benefits outlined for each aspect.

Another important dev tool we can take benefit of is the Performace tab in chrome dev tool, which I'll cover very soon in my next post.
