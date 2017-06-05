# Ensembl_Api_Demo_WebApp

# Readme

#### Prerequisite
##### You need npm package manager installed 
###### For linux ```sudo apt-get install npm```


##### You also need node.js installed in your machine 
###### For linux ```sudo apt install nodejs-legacy```


#### Install instructions

###### Clone the repository to your local folder via ssh or https
``` git clone https://github.com/priteshbhole/Ensembl_Api_Demo_WebApp.git```

###### Change into the project directory
``` cd Ensembl_Api_Demo_WebApp ```

###### Install all the project depencencies
run ```npm install ``` to install all the dependencies

###### Run local http server
run ```npm start``` to start a local http server

###### Browse to the application in your browser
http://127.0.0.1:8080


# Testing Strategies

###### Using frameworks like Jasmine, a Spy can be created to simulate a click event on the search button - which triggers the fetchData function.

Example code snippet as follows:
```
let button = document.getElementById('').click();
fixture.detectChanges();
expect(saveSpy.calls.any()).toBe(true, 'fetchData()/ fetch data to be called ');
    fixture.whenStable().then(() => {
      expect(fetchData).toHaveBeenCalled();
    });
```

#### Mocking the requests:
###### To test filter functionality
Requests can be mocked (Ex: API JSON response object) and can be used to verify if the fetchData function returns a similar object to that of the test function. In this case, it simulates the search filter response.
```
any = [response from api]

 it('check response', () => {
    fetchData();
      expect(response).toBe(any);
  });
 ```
 
######  To test request and response functionality 
```
  mockBackend.connections.subscribe(connection => {
            expect(connection.request.url).toBe('http://rest.ensembl.org/lookup/symbol/homo_sapiens/BRAF.json?;expand=1');
            let response = new ResponseOptions(
              {
                body: [{
            response body 
                }]
              });
            connection.mockRespond(new Response(response));

  httpGetRequest().then((_res) => {
            res = _res;
          });
          tick();
          expect(res[0]).toBe('response body');
          ```
