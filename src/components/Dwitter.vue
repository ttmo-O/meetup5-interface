<script lang="js">
    export default {
        name: 'Dwitter',
        // data: [],
        mounted() {
            var c = document.getElementById("c");

            c.width = 1920;
            c.height = 1080;

            var S = Math.sin;
            var C = Math.cos;
            var T = Math.tan;
            var R = function(r,g,b,a) {
                a = a === undefined ? 1 : a;
                return "rgba("+(r|0)+","+(g|0)+","+(b|0)+","+a+")";
            };
        
            var x = c.getContext("2d");
            var startT = +new Date();

            var a, b, d, e ,f, g, h, i, j, k, l, m, n, o, p, q, r, s, v, w, y, z;
            var A, F, W, X, Y;
            var λ, φ;

            function dwitter(opacity, slowdown, fcn) {
                return {
                    opacity: opacity,
                    slowdown: slowdown,
                    fcn: fcn,
                }
            }
        
            // ring
            function u11(t) {
                x.fillRect(0,0,q=c.width=2e3,q);for(i=q;i--;){r=160+(i/1e2)**4/t;z=6*S(i)+t*i/r;x.fillStyle="#fff";x.fillRect(1e3+C(z)*r,500+S(z)*r,5,5)}
            }
            
            // rain
            function u10(t) {
                l=c.width+=i=0;h=400;for(;++i<200;)for(j=a=(t+C(i))%2;j++<50;)x.fillRect(l*C(i*i)+~~a*(w=a*h-h)*C(j),(~~a?h:a*h)*(C(i)*C(i)+2)+w*S(j)/4,3,3)
            }
            
            // squares
            function u9(t) {
                (F=Z=>{for(x.fillStyle=R(W=1/Z*4e3,W/2,W/4),i=Z*Z*2;n=i%Z,m=i/Z|0,i--;n%2^m%2&&x.fillRect((n-t%2-1)*W,(S(t)+m-1)*W,W,W));Z&&F(Z-6)})(36)//rm
            }
            
            // fish
            function u8(t) {
                c.width=1920;for(i=16;i--;)x.ellipse(1e3+300*S(t+i*.1),500+50*C(t+i*.1),160*S(-i*.5)+160,50*S(i*.1)+5,1.6+.5*S(t*.5),9.5,0,6.3);x.stroke();
            }
            
            // triangles
            function u7(t) {
                for(i=w=3e3,a=b=g=333*T(t%9/7);j=(i^a*a)%4,i--;x.fillRect(a+=g+C(j*5+t)*g-a/2-w+g,b+=g+S(j*9+t)*g-b/2-w,s,s),w=2)x.fillStyle=R(s=w*9,w,s,.1)
            }
            
            // waves
            function u6(t) {
                for(d=256;--d;)for(X=-32;++X<32;x.fillRect(960+X*8e3/d,100+7e4/d-h,120,9))x.fillStyle=R(h=(C(a=d/9+t*6)+C(X/9+a/3))*35,g=h+C(X^d)*6+90,g/.8)
            }
            
            // tube
            function u5(t) {
                c.width^=0;for(i=9;i<2e3;i+=2)s=3/(9.1-(t+i/99)%9),x.beginPath(),j=i*7+S(i*4+t+S(t)),x.lineWidth=s*s,x.arc(960,540,s*49,j,j+.6),x.stroke()
            }
            
            // abstract
            function u4(t) {
                r=480;c.width=r*4;λ=0;for(φ=a=Math.PI/2;φ>-a;φ-=1/r){λ+=a;x.lineTo(C(φ)*S(λ-t)*r+2*r,(C(t=t+1/r)*S(φ)+S(t)*C(φ)*C(λ-t))*r+r)}x.stroke()
            }
            
            // pingpong
            function u3(t) {
                c.width=192;c.height=108;A=Math.abs;Y=A(t*99%176-88);X=A(t*139%376-188);x.F=x.fillRect;x.F(X,Y+7,3,3);x.F(187,Y+C(X/39)*29,5,20);x.F(0,Y-S(X/29)*22,5,20)
            }

            // planet
            function u2(t) {
                x.fillRect(0,0,i=2e3,i);for(t+=160;p=i&1,m=t/C(t/i)+p*(t/2+i%t),i--;)x.clearRect(960+m*S(n=t/9+i*i)*C(!p*i/t),540+m*C(n+p*2),s=3-C(n)*3,s)
            }

            // clock
            function u1(t) {
                c.width=2e3;for(a=i=629;i--;)s=-150/((i+t*60)%a),X=a*S(i*.31)*s+1e3,Y=a*C(i*.3)*s+500,x.fillRect(X,Y,s*9,s*9),x.lineTo(X,Y);x.stroke();
            }

            function u0(t) {
            }

            let arr = [
                // dwitter("0%", 1, u0),
                dwitter("15%", 5, u1),
                dwitter("25%", 10, u2),
                dwitter("15%", 5, u3),
                dwitter("15%", 5, u4),
                dwitter("15%", 10, u5),
                dwitter("20%", 10, u6),
                dwitter("15%", 5, u7),
                dwitter("25%", 5, u8),
                dwitter("25%", 5, u9),
                dwitter("25%", 1, u10),
                // dwitter("40%", 10, u11),
            ]

            let currOffset, curr, slowdown, u;

            function randomDwitter() {
                currOffset = Math.floor(Math.random() * arr.length);
                curr = arr[currOffset];
                c.style.opacity = curr.opacity;
                slowdown = curr.slowdown;
                u = curr.fcn;
                c.width=1920;
                c.height=1080;
            }

            randomDwitter();
            
            setInterval(randomDwitter, 30*1000);

            window.addEventListener("keydown", (ev) => {
                if (ev.key == "ArrowRight") {
                    randomDwitter();
                }
            }, { passive: true })
        
            function loop() {
                requestAnimationFrame(loop);
                u((new Date() - startT) / (slowdown*1000));
            };
        
            loop();
        }
    }
</script>

<template>
    <div class="fade-io-10">
        <!-- <img class="spinner" style="position: absolute; left: 42.40vw; top: 17.36vw; width: 15.5vw" src="logo-yuvarlak-beyaz-incecerceve.png" id="logo"> -->
        <canvas id="c"></canvas>
    </div> 
</template>

<style scoped>
#c {
  width: 100%;
  height: 100%;
  background-color: white;

  position: fixed;
  /* margin: auto; */
  top: 0;
  left: 0;
  /* opacity: 20%; */
  transition: 2s;
}
</style>