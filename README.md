# Expo `useAsyncStorage` Hook Error on Conditional Unmount

This repository demonstrates a bug related to the Expo `useAsyncStorage` hook and how it behaves when used within a conditionally rendered component.  If the component is unmounted before the asynchronous storage operation completes, it can result in warnings or crashes.  This is a common issue when dealing with asynchronous operations and component lifecycle management in React Native.

## Bug Description

The bug arises when the asynchronous operation of fetching data from `AsyncStorage` using `useAsyncStorage` isn't completed before the component that uses it is unmounted.  This leads to attempts to update a component that no longer exists in the React tree, causing warnings or even crashes.  The frequency of this bug depends largely on the speed of your storage operations and how quickly you trigger the unmounting of the component.

## Solution

The solution involves using the `useEffect` hook with a cleanup function to cancel the asynchronous operation if the component is unmounted before it completes.  This ensures that no further attempts are made to update the unmounted component.