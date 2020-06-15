# react-infinite-scroll-component [![npm](https://img.shields.io/npm/dt/react-infinite-scroll-component.svg?style=flat-square)](https://www.npmjs.com/package/react-infinite-scroll-component) [![npm](https://img.shields.io/npm/v/react-infinite-scroll-component.svg?style=flat-square)](https://www.npmjs.com/package/react-infinite-scroll-component)

A component to make all your infinite scrolling woes go away with just 4.15 kB! `Pull Down to Refresh` feature
added. An infinite-scroll that actually works and super-simple to integrate!

# install
```bash
  npm install --save react-infinite-scroll-component
  
  or
  
  yarn add react-infinite-scroll-component 

  // in code ES6
  import InfiniteScroll from 'react-infinite-scroll-component';
  // or commonjs
  var InfiniteScroll = require('react-infinite-scroll-component');
```

# using

```jsx
<InfiniteScroll
  dataLength={items.length} //This is important field to render the next data
  next={fetchData}
  hasMore={true}
  loader={<h4>Loading...</h4>}
  endMessage={
    <p style={{textAlign: 'center'}}>
      <b>Yay! You have seen it all</b>
    </p>
  }
  // below props only if you need pull down functionality
  refreshFunction={this.refresh}
  pullDownToRefresh
  pullDownToRefreshContent={
    <h3 style={{textAlign: 'center'}}>&#8595; Pull down to refresh</h3>
  }
  releaseToRefreshContent={
    <h3 style={{textAlign: 'center'}}>&#8593; Release to refresh</h3>
  }>
  {items}
</InfiniteScroll>
```

The `InfiniteScroll` component can be used in three ways.

- Specify a value for the `height` prop if you want your **scrollable** content to have a specific height, providing scrollbars for scrolling your content and fetching more data.
- If your **scrollable** content is being rendered within a parent element that is already providing overflow scrollbars, you can set the `scrollableTarget` prop to reference the DOM element and use it's scrollbars for fetching more data.
- Without setting either the `height` or `scrollableTarget` props, the scroll will happen at `document.body` like *Facebook's* timeline scroll.


# docs version wise
[3.0.2](docs/README-3.0.2.md)

# live examples

- infinite scroll (never ending) example using react (body/window scroll)
  - [![Edit yk7637p62z](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/yk7637p62z)
- infinte scroll till 500 elements (body/window scroll)
  - [![Edit 439v8rmqm0](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/439v8rmqm0)
- infinite scroll in an element (div of height 400px)
  - [![Edit w3w89k7x8](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/w3w89k7x8)
- infinite scroll with `scrollableTarget` (a parent element which is scrollable)
  - [![Edit r7rp40n0zm](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/r7rp40n0zm)

# props
name | type | description
-----|------|------------
**next** | function | a function which must be called after reaching the bottom. It must trigger some sort of action which fetches the next data. **The data is passed as `children` to the `InfiniteScroll` component and the data should contain previous items too.** e.g. *Initial data = [1, 2, 3]* and then next load of data should be *[1, 2, 3, 4, 5, 6]*.
**hasMore** | boolean | it tells the `InfiniteScroll` component on whether to call `next` function on reaching the bottom and shows an `endMessage` to the user
**children** | node (list) | the data items which you need to scroll.
**dataLength** | number | set the length of the data.This will unlock the subsequent calls to next.
**loader** | node | you can send a loader component to show while the component waits for the next load of data. e.g. `<h3>Loading...</h3>` or any fancy loader element
**scrollThreshold** | number &#124; string | A threshold value defining when `InfiniteScroll` will call `next`. Default value is `0.8`. It means the `next` will be called when user comes below 80% of the total height. If you pass threshold in pixels (`scrollThreshold="200px"`), `next` will be called once you scroll at least (100% - scrollThreshold) pixels down.  
**onScroll** | function | a function that will listen to the scroll event on the scrolling container. Note that the scroll event is throttled, so you may not receive as many events as you would expect. 
**endMessage** | node |  this message is shown to the user when he has seen all the records which means he's at the bottom and `hasMore` is `false`
**className** | string | add any custom class you want
**style** | object | any style which you want to override
**height** | number | optional, give only if you want to have a fixed height scrolling content
**scrollableTarget** | node or string | optional, reference to a (parent) DOM element that is already providing overflow scrollbars to the `InfiniteScroll` component. *You should provide the `id` of the DOM node preferably.*
**hasChildren** | bool | `children` is by default assumed to be of type array and it's length is used to determine if loader needs to be shown or not, if your `children` is not an array, specify this prop to tell if your items are 0 or more.
**pullDownToRefresh** | bool | to enable **Pull Down to Refresh** feature
**pullDownToRefreshContent** | node | any JSX that you want to show the user, `default={<h3>Pull down to refresh</h3>}`
**releaseToRefreshContent** | node | any JSX that you want to show the user, `default={<h3>Release to refresh</h3>}`
**pullDownToRefreshThreshold** | number | minimum distance the user needs to pull down to trigger the refresh, `default=100px`
**refreshFunction** | function | this function will be called, it should return the fresh data that you want to show the user
**initialScrollY** | number | set a scroll y position for the component to render with.
**key** | string | the key for the current data set being shown, used when the same component can show different data sets at different times, `default=undefined`
