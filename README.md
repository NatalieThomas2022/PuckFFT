# PuckFFT
const fs=1024; //must be power of 1
var w = new Waveform(fs,{doubleBuffer:true,bits:16});
var a = new Uint16Array(fs);
w.on("buffer", function(buf) {
  a.set(buf);
  E.FFT(a);
  var m=0,n=-1;
  for (var i=1;i<512;i++)if(a[i]>n)n=a[m=i];
  console.log(m.toFixed(0)+"Hz @ "+n);
});
w.startInput(D2,fs,{repeat:true});
