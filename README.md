# Unnecessary Re-renders in React 19 useEffect Hook

This repository demonstrates a common issue encountered in React 19 applications involving the `useEffect` hook. The `useEffect` hook is designed to perform side effects, but if not used correctly, it can lead to performance problems due to unnecessary re-renders.

## Problem

The provided `MyComponent` example uses `useEffect` to log the current count to the console.  Since the dependency array `[count]` includes `count`, the effect will run after *every* render, even though the logging itself doesn't affect the component's output. This results in redundant logging and potential performance degradation in more complex scenarios.

## Solution

The solution involves carefully selecting the dependencies of the `useEffect` hook.  If the effect doesn't need to depend on any state or props, pass an empty array (`[]`) as the second argument. This ensures that the effect only runs once after the initial render.