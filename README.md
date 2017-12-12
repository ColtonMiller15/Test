//position
var x=200;
var y=200;
//ship velocity
var xv=0;
var yv=0;
//ship rotation
var r=0;
//keys
var keys=[];
var bx=[];
var by=[];
var bn=0;
var bh=[];
var bxv=[];
var byv=[];
var bt=[];

var bx1=[];
var by1=[];
var bn1=0;
var bh1=[];
var bxv1=[];
var byv1=[];
var bt1=[];

 keyPressed = function() { keys[keyCode] = true; };
keyReleased = function() { keys[keyCode] = false; };
//turning speed
var ts=2;
//is the gun shooting?
var shoot=false;
//While Commands
var i=0;

while(i<20){
bx.push(0);    
by.push(0);
bxv.push(0);    
byv.push(0);
bt.push(0);
bx1.push(0);    
by1.push(0);
bxv1.push(0);    
byv1.push(0);
bt1.push(0);
//bn.push(0);
bh.push(false);
bh1.push(false);

i++;
}
i=0;


var scene=function(x1,y1,a,b){
rect(x1-a/2,y1-b/2,a,b);
};
var draw= function() {
background(255);
//acceleration
if(keys[LEFT]===true){
r-=ts;
} 
if(keys[RIGHT]===true){
r+=ts;
} 
if(keys[UP]===true){xv+=sin(r);
yv+=-cos(r);

}
x+=xv/20;
y+=yv/20;
//deceleration
if(xv>0){xv-=0.4;}
if(yv>0){yv-=0.4;}
if(xv<0){xv+=0.4;}
if(yv<0){yv+=0.4;}

//checking distance and stopping
if(dist(xv,xv,0,0)<=0.02){xv=0;}
if(dist(yv,yv,0,0)<=0.02){yv=0;}
//is space pressed?
if(keys[32]===true){shoot=true;}else{shoot=false;


}
pushMatrix();
translate(x,y);
rotate(r);
fill(0);
noStroke();
scene(0,0,15,15);
scene(0,0,40,5);
scene(-20,0,5,20);
scene(20,0,5,20);
fill(255, 0, 0);
//start

popMatrix();
if(shoot===true){
    bn+=0.1;
bn=bn%20;

}
while(i<20){
if(bx[i]<0){bx[i]=400;}
if(bx[i]>400){bx[i]=0;}
if(by[i]<0){by[i]=400;}
if(by[i]>400){by[i]=0;}
bx[i]+=bxv[i];
by[i]+=byv[i];
if(bh[i]===true){bt[i]++;
    ellipse(bx[i],by[i],5,5);

}
if(shoot===true){

if(round(bn)===i){bh[i]=true;}
if(bh[i]===true&&bt[i]<1){
bxv[i]=(sin(r)*5);    
byv[i]=-(cos(r)*5);    
xv-=sin(r)/10;
yv+=cos(r)/10;
}

}
if(bt[i]>100){bh[i]=false;}
if(bh[i]===false){bx[i]=x+sin(r+90)*20;
by[i]=y-cos(r+90)*20;
bt[i]=0;
}
i++;
}
i=0;
//end





while(i<20){
if(bx1[i]<0){bx1[i]=400;}
if(bx1[i]>400){bx1[i]=0;}
if(by1[i]<0){by1[i]=400;}
if(by1[i]>400){by1[i]=0;}
bx1[i]+=bxv1[i];
by1[i]+=byv1[i];
if(bh1[i]===true){bt1[i]++;
    ellipse(bx1[i],by1[i],5,5);

}
if(shoot===true){

if(round(bn)===i){bh1[i]=true;}
if(bh1[i]===true&&bt1[i]<1){
bxv1[i]=(sin(r)*5);    
byv1[i]=-(cos(r)*5);   
xv-=sin(r)/10;
yv+=cos(r)/10;
}

}
if(bt1[i]>100){bh1[i]=false;}
if(bh1[i]===false){bx1[i]=x+sin(r-90)*20;
by1[i]=y-cos(r-90)*20;
bt1[i]=0;
}
i++;
}
i=0;
//end
if(x<0){x=400;}
if(x>400){x=0;}
if(y<0){y=400;}
if(y>400){y=0;}
text(sin(r)*20,20,20);
text(cos(r)*20,20,40);


};
