# Comparing-HTML2PDF-mpdf-vivliostyle
Comparing the PDF generated with vivliostyle and mpdf, focussing on multicolumns, orphans and widows.

For automated PDF generation, take a look at http;//booktype.pro and give it a test ride at http://omnibook.pro

# Using vivliostyle on a headless ubuntu machine

To create a PDF on a headless server, you need to use electroshot. See: https://www.npmjs.com/package/electroshot

* Download the vivliostyle.jss package `vivliostyle-js-2016.7.zip` (tested with this version) from the website http://vivliostyle.com/en/products/#secProducts-download and unpack it.
* Follow their instructions and start the server with `./start-webserver`

Now you have vivliostyle running on the server.

To create a PDF on a headless server, you need to use electroshot. See: https://www.npmjs.com/package/electroshot
 
* Install node.js: `sudo apt-get install node.js`
* Install electroshot anywhere you want on your system in a directory: `npm install electroshot`
* For the headless server, install as it says on the electroshot site: `sudo apt-get update && sudo apt-get install -y libgtk2.0-0 libgconf-2-4 libasound2 libxtst6 libxss1 libnss3 xvfb`
* Start Xvfb `Xvfb -ac -screen scrn 1280x2000x24 :9.0 & export DISPLAY=:9.0`
  * In the command line, this might not bring you back to the prompt. Ctrl&C will do that for you.

Now it's about time to get the PDF generated.

* Go into the directory where you installed electroshot `cd node_modules/electroshot/bin/`
* This will create your PDF: `node ./electroshot.js 'http://127.0.0.1:8000/viewer/vivliostyle-viewer.html#x=../samples/github/completebook-2col-toc-orphanwidow/completebook-2col-toc-orphanwidow.html' 1024 --format pdf --pdf-margin none --out /home/micz/Documents/github/Comparing-HTML2PDF-mpdf-vivliostyle/completebook-2col-toc-orphanwidow --filename completebook-2col-toc-orphanwidow.pdf --delay 50000`

The delay needs to be long enough to go through the finished document afterwards to calculate the page numbers.