# ctlgen
<PRE> vevva ftp ctl generator

fs = require('fs');

var dist = 'dist/zip/';
var files = [];
var fileTmpl =
'USER=user@box.com\n\
PASSWORD=pass\n\
FILENAME='//+files[i]

fs.readdir(dist, (err, data) => {
  files = data;
  write();
});

function write() {
  for(var l = files.length; l -- ;){
    fs.writeFile((dist+files[l]).replace('.zip', '')+'.ctl', fileTmpl+files[l], (err)=> {
      if (err)
      console.log(err);
      console.log('done');
    });
  }
}
</PRE>

EXPEMPLE:

before:
dir
|_$1.zip
|_$2.zip
|_$3.zip

after:
dir
|_$1.zip
|_$2.zip
|_$3.zip
|_$1.ctl = 'fileTmpl+files[l]'
|_$2.ctl = 'fileTmpl+files[l]'
|_$3.ctl = 'fileTmpl+files[l]'


