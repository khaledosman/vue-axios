# vue3-axios
[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![dependencies Status](https://david-dm.org/khaledosman/vue3-axios/status.svg)](https://david-dm.org/khaledosman/vue3-axios)
[![devDependencies Status](https://david-dm.org/khaledosman/vue3-axios/dev-status.svg)](https://david-dm.org/khaledosman/vue3-axios?type=dev)
![npm](https://img.shields.io/npm/v/@khaledosman/vue3-axios/latest)
[![npm](https://img.shields.io/npm/dy/@khaledosman/vue3-axios.svg)]()
[![Build Status](https://travis-ci.org/khaledosman/vue3-axios.svg?branch=master)](https://travis-ci.org/khaledosman/vue3-axios)


Composition API & Vue component helpers for making API requests and rendering the results in vue 3

## Guide

The library offers 3 different layers of abstraction for making API requests that can be used separately:

1. `useAPI` is a hook that can be used in any component and gives the user full control of the request (cancellation, caching, refetch, error & loading states)
2. `AxiosComponent` is an Async component that uses the `useAPI` hook to render/mount itself only when the initial request is done and the results are ready. it delegates rendering of error / loading or results via named slots.
3. `VueAxiosComponent` Which uses `AxiosComponent` to provide generic error & loading states and uses the new `Suspense` API to handle rendering of the Async Component. it delegates rendering of results via a named slot.

the `useAPI` hook uses `cachedGet` function for get requests which provides two different strategies: Online first, and offline first:

- In Online first mode the request goes first to the network then saves the results in cache, or fallbacks to the cache if the user is offline or the network request fails, this is best-suited for content that needs to be always fresh.

- In Offline first mode the results are returned from the cache first, then a network request is done in the background to update the cache for next use or go to the network if there're no results in cache. This is best suited for apps that need to work under any network condition like bad Wifi / Slow internet or even completely offline with the compromise of less fresh data (i.e twitter, facebook, instagram). It also offers the best performance since the user can see results instantly without even the need for a loading state.

## Example

- `HelloWorldComponent` is a use case example, which show cases how `VueAxiosComponent` can be used
- `VueAxiosComponent` is an example, which show cases how `AxiosComponent` can be used
- `AxiosComponent` is an example which show cases how `useAPI` hook can be used
