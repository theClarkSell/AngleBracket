

---
## Module 4 - Web Storage

### I. Local Storage

1. Open "4- JavaScript API/labs/web_storage/begin/order.html" in a browser. This page should look similar to the page from the forms module in Lab #1.

2. Open js/storage.js and add the following function, which should fire when the user clicks the "Save for Later" button:

		$('#saveForLater').click(function () {}); 

3. Accessing local storage is as simple as calling `window.localStorage`. Items can be access like `window.localStorage["name"]` or as an expando, `window.localStorage.name`. Add the following inside the function from step #2 to save the order information to the localStorage object:

		window.localStorage.name = $('#orderName').val();
		window.localStorage.email = $('#orderEmail').val();
		window.localStorage.webSite = $('#orderWebsite').val();
		window.localStorage.phone = $('#orderTelephone').val();
		window.localStorage.delivery = $('#deliveryDate').val();
		window.localStorage.address = $('#orderShipping').val();
		window.localStorage.quantity = $('#orderQty').val();
		$('#saveForLater').val('Saved!');

4. Refresh the page and enter some data in the fields and click "Save for later"

5. Open up the developer tools in your browser and inspect the local storage. Some browsers have a visual inspector, but all browsers allow you to open the console tab and type `window.localStorage` to see the contents of the object. Do so and make sure that your data has been saved.

6. Refresh the page. The fields are blank, so lets use the information in local storage to re-populate these when the user returns to the page. Place the following outside of the `$('#saveForLater')` function in step #2:
	
		$('#orderName').val(window.localStorage.name);
		$('#orderEmail').val(window.localStorage.email);
		$('#orderWebsite').val(window.localStorage.webSite);
		$('#orderTelephone').val(window.localStorage.phone);
		$('#deliveryDate').val(window.localStorage.delivery);
		$('#orderShipping').val(window.localStorage.address);
		$('#orderQty').val(window.localStorage.quantity);

5. Now refresh the page. You saved data should now be in the form. To verify that localStorage is persistent, close the browser, re-open and return to this page.

### II. Session Storage

1. Where Local Storage is persistent, Session Storage only lasts for the user's current session (for instance, in a single tab). Let's see how this works by adding a Session variable that displays to the user the time the order was initiated. Add the following to the end of js/storage.js:

		if (!window.sessionStorage.orderStamp) {
			window.sessionStorage.orderStamp = formatDate(new Date());
		}
		$('#time').text("Order initiated on: " + window.sessionStorage.orderStamp);

	Note that `sessionStorage` is accessed similarly to local storage, and its properties can also be accessed in expando fashion.

2. Refresh the page, and take note of the timestamp on the form. Refresh the page several times, and notice that the timestamp does not change.

3. Now, open another tab and navigate to the same page. Notice that the timestamp is different than the original tab, but also stays the same when the page is refreshed several times.

### ***[Extra Credit]*** Check out the Modernizr [Polyfills and shims page](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills) for a Web Storage polyfill, and add it to the page.


___

# Resources
