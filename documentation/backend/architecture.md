## Overview

The webpage is created in a way that makes each component dynamic. The s3 bucket hosts all the static components which have pieces of code connecting back through the API gateway (emailing out for example). Below is the architecture that we ended up going with. It is not exactly the same, but you should be able to get the idea.

![screen shot 2018-10-17 at 3 18 42 pm](https://user-images.githubusercontent.com/20977403/50653142-8edd9080-0f56-11e9-99e0-72beb0a05fca.png)

The main difference that we have is there are more lambda functions that what appear in this architecture diagram and there is no user authorization on the client side.

## Ideas not implimented yet

* Instead of having client authorizations, we have a check on data entry if the sata is already contained in the database. If it is then we would need to check or push if the user wants to modify these numbers.
* We need to have the lambda functioin check if the numbers entered into the webpage form make sense.