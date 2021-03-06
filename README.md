# B&R SiteManager Demo for Azure IoT
This repo contains code for a web application, which can read several data from IoT hub and show the real-time data in a line chart on the web page.

The code is based on https://github.com/Azure-Samples/web-apps-node-iot-hub-data-visualization

## Browser compatible
| Browser | Least Version |
| --- | --- |
| IE | 10 |
| Edge | 14 |
| Firefox | 50 |
| Chrome | 49 |
| Safari | 10 |
| Opera | 43 |
| iOS Safari | 9.3 |
| Opera Mini | ALL |
| Android Browser | 4.3 |
| Chrome for Android | 56 |

## Run a SiteManager to send data to the IoT Hub
You need a B&R SiteManager to collect field data from your machines and send them to the IoT Hub!
See [B&R Website](https://www.br-automation.com/de-at/technologie/industrial-iot) for further information!

## Add new consumer group to your event hub
Go to [Azure Portal](https://portal.azure.com) and select your IoT hub. Click `Endpoints -> Events`, add a new consumer group and then save it.

## Deploy to Azure web application
Go to [Azure Portal](https://portal.azure.com) to create your own Azure web app service. Then do the following setting:

* Go to `Application settings`, add key/value pairs `Azure.IoT.IoTHub.ConnectionString` and `Azure.IoT.IoTHub.ConsumerGroup` to `App settings` slot.
* Go to `Deployment options`, select `Github repository` to deploy your web app.
* Go to `Deployment credentials`, set your deploy username and password.
* In the `Overview` page, note the `GitHub project` URL.
* The code will then be synchronized to your WebApp
* You can now view the page to see the real-time data chart.

## Local deploy
* Open a console and set the following environment variable:
  * `set Azure.IoT.IoTHub.ConnectionString=<your connection string>`
  * `set Azure.IoT.IoTHub.ConsumerGroup=<your consumer group name>`
* Open ./public/javascripts/index.js, and change the code around line 69

    from
    ```js
    var ws = new WebSocket('wss://' + location.host);
    ```
    to
    ```js
    var ws = new WebSocket('ws://' + location.host);
    ```
* `npm install`
* `npm start`
