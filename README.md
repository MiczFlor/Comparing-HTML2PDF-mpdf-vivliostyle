# Comparing-HTML2PDF-mpdf-vivliostyle
Comparing the PDF generated with vivliostyle and mpdf, focussing on multicolumns, orphans and widows.

# Using vivliostyle on a headless linux

To create a PDF on a headless server, you need to use electroshot. See: https://www.npmjs.com/package/electroshot

* Install node.js: `sudo apt-get install node.js`
* Install electroshot anywhere you want on your system in a directory: `npm install electroshot`
* For the headless server, install: `sudo apt-get update && sudo apt-get install -y libgtk2.0-0 libgconf-2-4 libasound2 libxtst6 libxss1 libnss3 xvfb`
* `cd node_modules/electroshot/bin/`
* Start Xvfb `Xvfb -ac -screen scrn 1280x2000x24 :9.0 & export DISPLAY=:9.0`
* `node ./electroshot.js 'http://127.0.0.1:8000/viewer/vivliostyle-viewer.html#x=../samples/github/completebook-2col-toc-orphanwidow/completebook-2col-toc-orphanwidow.html' 1024 --format pdf --pdf-margin none --out /home/micz/Documents/github/Comparing-HTML2PDF-mpdf-vivliostyle/completebook-2col-toc-orphanwidow --filename completebook-2col-toc-orphanwidow.pdf --delay 50000`

The delay needs to be long enough to go through the finished document afterwards to calculate the page numbers.