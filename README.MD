- find paths from js file 

```
cat loaction.js|  grep -o '"/[^"]*"' | sort -u
```
- Js New Paths
```
javascript:(function(){var scripts=document.getElementsByTagName("script"),regex=/(?%3C=(\%22|\%27|\`))\/[a-zA-Z0-9_?&=\/\-\#\.]*(?=(\%22|\'|\%60))/g;const%20results=new%20Set();for(var%20i=0;i%3Cscripts.length;i++){var%20t=scripts[i].src;if(t!==%22%22){fetch(t).then(function(response){return%20response.text();}).then(function(text){var%20matches=text.matchAll(regex);for(let%20match%20of%20matches){results.add(match[0]);}}).catch(function(error){console.log(%22An%20error%20occurred:%22,error);});}}var%20pageContent=document.documentElement.outerHTML;var%20matches=pageContent.matchAll(regex);for(const%20match%20of%20matches){results.add(match[0]);}setTimeout(function(){var%20uniqueSortedResults=[...results].sort();var%20newWindow=window.open('','_blank');newWindow.document.write('%3Cpre%3E'%20+%20uniqueSortedResults.join(%22\n%22)%20+%20'%3C/pre%3E');},3000);})();
```
- JavaScript URLs
```
javascript:(function(){var scripts=document.getElementsByTagName('script');var jsFiles=[];for(var i=0;i<scripts.length;i++){var src=scripts[i].src;if(src){jsFiles.push(src)}}if(jsFiles.length===0){alert('No JavaScript files found on this page.')}else{var jsFileList=jsFiles.join('\n');var newWindow=window.open();newWindow.document.write('<pre>'+jsFileList+'</pre>')}})();
```
- Js Token
```
javascript:(function(){var regex=/([A-Za-z0-9\-_]{10,})(?=\s*[:=]\s*[%27%22]?[A-Za-z0-9\-_]{10,}[%27%22]?)/g,scripts=document.getElementsByTagName(%22script%22),results=new%20Set();for(var%20i=0;i%3Cscripts.length;i++){var%20t=scripts[i].src;if(t!==%22%22){fetch(t).then(function(response){return%20response.text();}).then(function(text){var%20matches=text.matchAll(regex);for(let%20match%20of%20matches){results.add(match[0]);}}).catch(function(error){console.log(%22An%20error%20occurred:%22,error);});}}var%20pageContent=document.documentElement.outerHTML;var%20matches=pageContent.matchAll(regex);for(const%20match%20of%20matches){results.add(match[0]);}var%20uniqueSortedResults=[...results].sort();var%20newWindow=window.open(%27%27,%27_blank%27);newWindow.document.write(%27%3Cpre%3E%27%20+%20uniqueSortedResults.join(%22\n%22)%20+%20%27%3C/pre%3E%27);})();
```
- Filter Domain
```
javascript:(function(){var regex=/(?:https?:\/\/)?(?:www\.)?([a-zA-Z0-9\-]+\.[a-zA-Z0-9\-]+\.[a-zA-Z]{2,})(?:\.[a-zA-Z]{2,})*(?:\/[^\s]*)?/g,scripts=document.getElementsByTagName(%22script%22),results=new%20Set();for(var%20i=0;i%3Cscripts.length;i++){var%20t=scripts[i].src;if(t!==%22%22){fetch(t).then(function(response){return%20response.text();}).then(function(text){var%20matches=text.matchAll(regex);for(let%20match%20of%20matches){results.add(match[1]);}}).catch(function(error){console.log(%22An%20error%20occurred:%22,error);});}}var%20pageContent=document.documentElement.outerHTML;var%20matches=pageContent.matchAll(regex);for(const%20match%20of%20matches){results.add(match[1]);}var%20filteredResults=[...results].filter(domain=%3Edomain.includes(%22CHANGEME%22)).sort();var%20newWindow=window.open(%22%22,%27_blank%27);newWindow.document.write(%22%3Cpre%3E%22+filteredResults.join(%22\n%22)+%22%3C/pre%3E%22);})();
```
- IP4
```
javascript:(function(){var regex=/\b(?:\d{1,3}\.){3}\d{1,3}\b/g,scripts=document.getElementsByTagName(%22script%22),results=new%20Set();for(var%20i=0;i%3Cscripts.length;i++){var%20t=scripts[i].src;if(t!==%22%22){fetch(t).then(function(response){return%20response.text();}).then(function(text){var%20matches=text.matchAll(regex);for(let%20match%20of%20matches){results.add(match[0]);}}).catch(function(error){console.log(%22An%20error%20occurred:%22,error);});}}var%20pageContent=document.documentElement.outerHTML;var%20matches=pageContent.matchAll(regex);for(const%20match%20of%20matches){results.add(match[0]);}var%20uniqueSortedResults=[...results].sort();var%20newWindow=window.open(%27%27,%27_blank%27);newWindow.document.write(%27%3Cpre%3E%27%20+%20uniqueSortedResults.join(%22\n%22)%20+%20%27%3C/pre%3E%27);})();
```