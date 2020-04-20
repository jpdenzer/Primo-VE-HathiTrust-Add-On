# Primo-VE-HathiTrust-Add-On

## Description
Primo VE HathiTrust Add-On. This add-on is modified from <a href="https://github.com/UMNLibraries/primo-explore-hathitrust-availability">primo-explore-hathitrust-availability</a> to work with Primo VE.


## Add code to custom.js file
1. Add the js entire code from <b>Primo-VE-HathiTrust-Add-On.js</b>into your main function in the Primo <b>custom.js</b> file

2. Modify the following in your <b>custom.js</b>:
  ```js
    var app = angular.module('viewCustom', ['angularLoad');
  ```
3. Add  the <b>hathiTrustAvailability</b> module to <b>app</b>:
  ```js
  var app = angular.module('viewCustom', ['angularLoad', 'hathiTrustAvailability']);
  ```
4. Add the <b>SearchResultAvailabilityLineAfterController</b>
```js
app.controller('SearchResultAvailabilityLineAfterController', [function () {
 var vm = this;
}]);
```

## Adding component for Browzine support.
#### This step is for Browzine customers with Browzine Add-On enabled
1. Modify the following Browine code in your <b>custom.js</b>:
```js
app.component('prmSearchResultAvailabilityLineAfter', {
  bindings: { parentCtrl: '<' },
  controller: 'prmSearchResultAvailabilityLineAfterController'
});
```
2. Add the <b>hathi-trust-availability-studio</b> template to <b>prmSearchResultAvailabilityLineAfter</b>.
```js
//BrowZine and HathiTrust -START-
  app.component('prmSearchResultAvailabilityLineAfter', {
    bindings: { parentCtrl: '<' },
	template: '<hathi-trust-availability-studio parent-ctrl="$ctrl.parentCtrl">',
    controller: 'prmSearchResultAvailabilityLineAfterController'
  });
  //BrowZine and HathiTrust -END-
```

## Adding component
#### This step is for <b>Non Browzine</b> customers
1.  Add the <b>hathi-trust-availability-studio</b> template to <b>prmSearchResultAvailabilityLineAfter</b>the code.
```js
    app.component('prmSearchResultAvailabilityLineAfter', {
      bindings: { parentCtrl: '<' },
  	template: '<hathi-trust-availability-studio parent-ctrl="$ctrl.parentCtrl">',
      controller: 'SearchResultAvailabilityLineAfterController'
    });    
```

## Set var for HathiTrust members and Public Domain and Copyrights
1. Set true or false based on if you are HathiTrust member.</br>
true is for <b>Non</b> HathiTrust Member</br>false is for HathiTrust member
```js
//If NOT hathitrust member set if to true
//If hathitrust member set if to false
	var nonhathiTrustMember = true;
```

## Customize HathiTrust message for Primo (optional)
1. Modify the following text with your own <i>Full Text May be Available at HathiTrust</i>
```js
angular.module('hathiTrustAvailability', []).value('hathiTrustMsg', 'Full Text May be Available at HathiTrust').constant('hathiTrustBaseUrl', "https://catalog.hathitrust.org/api/volumes/brief/json/").config(['$sceDelegateProvider', 'hathiTrustBaseUrl', function ($sceDelegateProvider, hathiTrustBaseUrl) {
```

## Add code to custom.css file
1. Add the css code from <b>Primo-VE-HathiTrust-Add-On.css</b> into your Primo <b>custom.css</b> file
```css
span.umnHathiTrustLink {
  margin-left: -5px;
}
span.umnHathiTrustLink md-icon svg {
  height: 1.2em;
  filter: grayscale(100%);
}
span.umnHathiTrustLink:hover md-icon svg {
  filter: grayscale(0%);
}
```

## Repackage your <b>customview</b> and upload it to Alma
