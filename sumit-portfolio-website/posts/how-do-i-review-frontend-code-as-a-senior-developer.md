---
title: How do I review Frontend Code as a Senior Developer
slug: how-do-i-review-frontend-code-as-a-senior-developer
createdAt: '2026-05-02T15:37:31.535Z'
updatedAt: '2026-05-02T15:41:54.468Z'
metadata:
  title: How do I review Frontend Code as a Senior Developer
  description: ''
  heroImage: 'https://i.imgur.com/n7VlWXq.png'
  draft: true
  publishedAt: '2025-03-03T15:36:00.000Z'
description: ''
heroImage: 'https://i.imgur.com/n7VlWXq.png'
draft: false
publishedAt: '2025-03-03T10:06:00.000Z'
---
In my journey as a frontend developer, I’ve made my fair share of mistakes—each one teaching me valuable lessons. Over the years, these experiences have shaped the way I approach code reviews. At the end of the day, they have helped me become a better developer.

When reviewing frontend code, I focus on a few common patterns that significantly impact performance, readability, scalability, and maintainability. By keeping these patterns in mind, developers can consistently improve their code quality.

## **Minimizing DOM Nodes**

A complex DOM structure can slow down rendering and impact performance. Look for unnecessary `<div>` elements, deeply nested structures, or redundant wrappers that can be optimised.

### **Why?**

- Deeply nested DOM trees trigger excessive reflows because changes to a parent element require recalculating positions and sizes for all child elements. The more elements the browser has to compute, the slower the UI response. Minimize unnecessary nested elements.
    
- Large DOM trees increase search complexity when manipulating elements via JavaScript (`document.querySelectorAll`, `getElementById`, etc.). Even React’s **reconciliation algorithm** must traverse the virtual DOM and compare it with the actual DOM before making updates, which can slow down the process.
    
- Heavy DOM manipulation often causes animation and transition lags.
    
- More DOM nodes mean higher memory consumption and increased **garbage collection**, leading to janky performance, especially on low-end devices.
    
- If reducing DOM size isn't an option, consider **virtualization** (e.g., `react-window`, `react-virtualized`) for rendering large lists instead of loading all elements at once.
    

**Tip:** Use `<Fragment>` instead of unnecessary `<div>` wrappers whenever possible and optimise list rendering by using the correct `key` values.

## **CSS Optimization**

- **Avoid complex selectors** (e.g., `div > ul li:first-child`) as they require more computations. Deeply nested elements force the browser to evaluate multiple styles before rendering.
    
- Be cautious with **`:nth-child(n)`** and **`:hover`** on large lists, as they can trigger expensive repaints.
    
- **Prefer CSS variables over inline styles** to reduce recalculations.
    
- **Reduce repaint and reflow issues** by avoiding layout thrashing (e.g., reading and writing to the DOM in quick succession).
    
- **Use modern layout techniques like Grid and Flexbox** instead of relying on excessive margins and paddings.
    

## **Take Advantage of Event Delegation**

Attaching event listeners to multiple elements increases memory consumption and CPU cycles. Instead, add an event listener to a parent element and handle events using **event delegation**.

## **Use Try-Catch for API Calls**

Even if your code is perfect, network issues, incorrect data, or server downtime can break your app. Handling failures gracefully improves the user experience.

### **Solution:** Always use `try-catch` for async API calls and provide meaningful fallback UI when data is unavailable.

```js
async function fetchData() {
  try {
    const response = await fetch("https://api.example.com/data");
    if (!response.ok) throw new Error("Failed to fetch data");

    return await response.json();
  } catch (error) {
    console.error("API Error:", error);
    return null; // Handle gracefully
  }
}
```

### **Optimise API Calls: Parallel vs. Sequential Requests**

Instead of fetching data sequentially, which can slow down the application, use `Promise.all()` to execute multiple requests in parallel.

```js
async function fetchUserData(userId) {
  const [user, posts, notifications] = await Promise.all([
    fetch(`/api/user/${userId}`).then((res) => res.json()),
    fetch(`/api/user/${userId}/posts`).then((res) => res.json()),
    fetch(`/api/user/${userId}/notifications`).then((res) => res.json()),
  ]);

  return { user, posts, notifications };
}
```

#### **Performance Comparison**

Approaches - Execution Time (Assuming 3 API Calls Each Take 500ms)
- Sequential: **1.5 seconds** (500ms + 500ms + 500ms)
- Parallel: **~500ms** (Fastest API call determines the time)


## **Check for Potential Runtime Errors**

Accessing undefined properties can cause crashes. Use default values and optional chaining (`?.`) to prevent errors.

```js
const user = apiResponse?.user ?? {};
console.log(user.name ?? "Guest");

const newArray = [...(incomingArray ?? [])];
```

## **Couple of POints to optimise React Components**

- Keep components **small and focused** on a single responsibility.
    
- Avoid unnecessary `useState` and `useEffect` hooks.
    
- Use `React.memo` to prevent redundant re-renders.
    
- Optimise expensive calculations with `useMemo` and `useCallback`.
    
- Avoid excessive state updates within `useEffect`.
    
- Use **context providers** or **state management solutions** to avoid prop drilling.
    
- **Lazy load images and components** to improve initial load times.

## **Writing Clean and Modular Methods**


When reviewing frontend code, we should ensure that newly introduced methods are well-structured, readable, and do a single responsibility and avoid doing multiple things.

example - A function that fetches data, manipulates it, and updates the UI all at once.

```js
function loadUserData(userId) {
  fetch(`/api/user/${userId}`)
    .then((response) => response.json())
    .then((data) => {
      document.getElementById("user-name").textContent = data.name;
      document.getElementById("user-email").textContent = data.email;
    })
    .catch((error) => console.error("Error loading user data", error));
}
```

It is better this way -

```js
async function fetchUserData(userId) {
  try {
    const response = await fetch(`/api/user/${userId}`);
    return await response.json();
  } catch (error) {
    console.error("Error fetching user data", error);
    return null;
  }
}

function updateUserUI(userData) {
  if (!userData) return;
  document.getElementById("user-name").textContent = userData.name;
  document.getElementById("user-email").textContent = userData.email;
}

async function loadUserData(userId) {
  const userData = await fetchUserData(userId);
  updateUserUI(userData);
}
```

Use meaningful variable and function names. Please Keep functions small and modular. Use technique like **Memoization** to **cache** previously computed results so that expensive computations are **not repeated unnecessarily**.

```js
const memoizedFactorial = (() => {
  const cache = {};

  return function factorial(n) {
    if (cache[n]) return cache[n];
    console.log("Calculating...");
    return (cache[n] = n <= 1 ? 1 : n * factorial(n - 1));
  };
})();

console.log(memoizedFactorial(5)); // Calculates once
console.log(memoizedFactorial(5)); // Returns from cache instantly

```

## **Advanced Optimization Techniques**

- **Memoization:** Cache previously computed results to avoid unnecessary recalculations.
    
- Use **Debounce** and **Throttling** to optimise frequent user interactions.
    
- Keep functions **small and modular** (<30 lines). Refactor large blocks into **helper functions**. Remember a small code serving a single responsibility is always better than a large block of code doing multiple things.
    
- **Write unit tests** to catch regressions early, if you do it right now, it will keep you and the team out of bugs.
    

## **Bonus Tips**

- If you are a code owner, then use tools like chrome dev-tooks (performance, Lighthouse) and React Profiler to see page performance before raising any major feature request.
- Do not write the solution in the review, instead give the developer clear instructions to fix a potential problem.
- **Encourage Best Practices:** Share resources and examples to help the team grow collectively.

The list may vary from developer to developer, stack to stack, and company to company. However, I wanted to highlight some common challenges that I’ve frequently seen developers encounter.

As a senior developer, reviewing frontend code goes beyond just catching syntax errors—it’s about ensuring high performance, clean and concise code, and maintainability. By focusing on key patterns, we can help developers write code that is efficient, readable, and built to scale.

What other tips or patterns do you keep in mind during code reviews?

