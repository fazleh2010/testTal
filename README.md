# Publish and link your terminology
### Instruction for publish your terminology and link your with other terminology
Prerequisite
docker
Note: An example file of terminology (solar.tbx) and mapping file can be found in this repository.

1. install docker
```
https://docs.docker.com/engine/install/
```
2. downlaod and install docker image
```
docker pull fazleh/term-a-llod:latest
docker run -p 8080:8080 -it fazleh/term-a-llod:latest
```
3. Go to home page at http://localhost:8080/status?view=status 
4. publishing your terminology.
```
curl -X POST --progress-bar \
    --verbose \
    -F 'upload=@solar.tbx' \
    -F 'mapping=@mappings.default' \
    -F 'graph=tbx2rdf_graph' \
    -F 'datanamespace=http://tbx2rdf.lider-project.eu/data/YourNameSpace/' \
    "http://localhost:8080/initialize"
    
    here solar.tbx is the terminology file and mapping file (mappings.default)
```
5. Check your terminology
 ```
b) got o http://localhost:8080/describe
   In the browser,you can see the terms in sorted alphabet order. Note: currently term link does not work. It is under construction. 
a) go to http://localhost:8080/status?view=sparql and press query button
```
6. Linking your terminology with other terminology.
```
curl -d "endpoint=https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql" \
          -H "Content-Type: application/x-www-form-urlencoded" \
          -X POST "http://localhost:8080/link"      
          
 here https://webtentacle1.techfak.uni-bielefeld.de/tbx2rdf_intaglio/sparql is sparql endpoint of the terminology you wanted to link.         
 ```
7. Check term links
  go to http://localhost:8080/status?view=search
 ```
a) an example of linked term is 'hole' 
b) type 'hole' in search box
```
### The system snapshot can be seen from this [link](https://github.com/fazleh2010/term-a-llod-demo/blob/master/GuidleLIne.pdf)
### Current limitation
a) the current version of the system is not tested for very large terminology such as IATE. The matching algorithm writting for two terminologies currently check one by one. It needs to be changed.
b) Term pages of the browser is not working now. They will be linked to http://localhost:8080/status?view=search.

---

## Author
* **Mohammad Fazleh Elahi**
* **Frank Grimm**
* **Dr. Philipp Cimiano**



---
