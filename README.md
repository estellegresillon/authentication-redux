### Authent with 0Auth

Doc: 
https://developers.google.com/api-client-library/


Create credentials for an app and get client id:
http://console.developers.google.com


Add Google script in HTML <head>
```
<script src=« https://apis.google.com/js/api.js »></script>
```
Check if the script works by typing gapi in console


Get a user status (logged in/logged out):
```
gapi.auth2.getAuthInstance().isSignedIn.get()
```
Returns a boolean


Open the sign in modal/sign out:
```
gapi.auth2.getAuthInstance().signIn()
gapi.auth2.getAuthInstance().signOut()
```


Add an event listener
```
gapi.auth2.getAuthInstance().isSignedIn.listen()
```
Check user's status at render


Get a Google ID:
```
gapi.auth2.getAuthInstance().currentUser.get().getId()
```

## Init example :

```
window.gapi.load(‘client:auth2’, () => {
	window.gapi.client
		.init({ 
			clientId: ‘YOUR CLIENT ID CONFIGURE IN GOOGLE APPS’,
			scope: ‘email’
		})
		.then(() => {
			this.auth = window.gapi.auth2.getAuthInstance()
			this.setState({ isSignedIn: this.auth.isSignedIn.get() })			this.auth.isSignedIn.listen(this.onAuthChange)
		)}
	})
}
```