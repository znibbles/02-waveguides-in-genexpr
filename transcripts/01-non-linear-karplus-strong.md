## Digital Waveguides Review

Digital waveguides are a class of algorithms that model how acoustic waves travel through a medium. They thus belong to the more simple proponents of physical modeling algorithms. 

In general, they are implemented using two opposing delay lines, to indicate how waves are reflected at boundaries and travel back and forth through the medium, an excitation signal bringing energy into the system, a pickup withdrawing energy, and a lowpass filter representing friction loss at the boundaries.

The simplest case of string modeling is called the Karplus-Strong algorithm, and consists only of a tuneable, feedbacked delay line with a damping filter. 

## Spicing up

Although for this very simple process the output is astoundingly good, such systems often sound sterile and too polished, because they lack the nonlinearities introduced by material imperfections in the real world.

It is those imperfections, however, that provide realism and present a valuable opportunity for sound design at the same time. We will look at a way to model a string termination as an imperfect spring.

So, at the string boundary, after the delay line, we add a nonlinear allpass filter, that is, an allpass filter with modulatable coefficients. We start out by implementing a simple first order allpass filter as shown in this block diagram. ![](http://peabody.sapp.org/class/st1/lab/prog6/Allpass1-flowgraph.gif)
([http://peabody.sapp.org/class/st1/lab/prog6/](http://peabody.sapp.org/class/st1/lab/prog6/))

We implement the modulation by specifying one coefficient first, and a sample and hold logic to multiply that coefficient. While this provides a glimpse of what we are able to do here, it is a more physically correct modeling we're after here, that is, a string terminated by a nonlinear spring, which can be modelled by two separate springs with different stiffness coefficients.

Thus, we add a second coefficient to our allpass and use both in an alternating manner, based on the zero crossings of the input. In other words, whenever a zero crossing occurs, we switch the coefficient from one to the other. Since nonlinearities can introduce instability into a system, we minimize the probability of them occurring by modulating when the least amount of energy is in the system.

And here the fun part begins: Try experimenting with different combinations of excitation signals and modulators - but don't be surprised when the system grows unstable at some point, it has happened to me quite a few times ;)

For a scientific deduction of the algorithm, see [https://quod.lib.umich.edu/cgi/p/pod/dod-idx/traveling-wave-implementation-of-a-lossless-mode-coupling.pdf?c=icmc;idno=bbp2372.1994.106;format=pdf](https://quod.lib.umich.edu/cgi/p/pod/dod-idx/traveling-wave-implementation-of-a-lossless-mode-coupling.pdf?c=icmc;idno=bbp2372.1994.106;format=pdf)


```
----------begin_max5_patcher----------
3264.3oc6cssbihiF95jmBFW6E6NaRVcfiSUyVce+T6KPWckBaq3vzXfBvYR
ltl9YeER.lSBjv.1iStwIHIP5+6+n9kP78auY05vWIIqz9EsuncyMe+1atgU
TVA2je8Mq1695Fe2DVyV8jeXvg8qtiWE8e8B7Ior5f4E5sk0xv0+983hFF4l
t4YufcOFS1jx6OCr4Cf6zbvY+Z.x9Egd.n80iO6vCoEObTdoIou4SXO+iO5X
28jTR7ij.207JA40we.ouEQ38I8lzVs1MX2pxt4ov38trgjYVA+0s2l8ycRB
G6IIIt6HEikTxqrG0JWj1+.1IJgZiR5CiRPLCfzgC.SPgvTanP6qiffihIIj
To4+18QZNbpAy9CDvoPfPZSWdZqXTpsxKf8m5ET1A7hebqapagRPIcy6+0j3
JzFsris03tbhTO64VnXv9O2rtBwonhl4jUmu2KjG145E7ips7dzClXaan4wV
ajUed+WRF3JM.A6tWAOXUoQHQMxw9Xqv.gspRGhsxpKMb2NJ5WNjfUZP2Ok6
oOFcGtvVgjV2fL5h.jMAx.xHCC4f4yFNOJ06htUR0aqdTugF1L8ZclRd4uJa
3RI66bs6QP3Aj+fRQsriS633vLgLfrFywF8hIFLibNY+ZglNi449zFAgqnCc
POTmNDeE6QGpfGcj4vvTtKcNZcNcoyLWxv6eHqX.puPVf.yGn1pPPl7sQoy8
AnuVTiuWR5RHSmY8VHwfQF+8WlVQ7.1CdfvVWu53OQHaW6t4aJnoCsFV3IWS
2x7bqoKht25tOhDnBUqOrHRAUCuTo5fvThJzbeSlEZZWglMN6zbQPsxowaLL
kc1T3GAwmDQG8wgIaBiH+PZ1aeSUE5fxbok8GVXrLHAkM+0IgAWz3vfvp271
v8zIwvaFH2MJ2Q5zEf6NRf7d8WUZ8MHMfxMY074XOW+9LBxmdOG5v1SmlQh2
t.ZOWwmPPZh2explE6QkgDeBlUl24pm77IuPhS7BCpNA+UtQQUJt9TU2696g
rGjU4LUoHFuHbYQwjW7JteixRcio.SJEUNDyoqWsKBRL6wDtkDGbviMTJmo7
sEOvRrjMMJK1zGf4AXYZiOhlTofcaB84CoLoFm6p7CrZCIa8Ry3TReCq24Gt
4ajsUzbobEpiCu.VdTBRcSyI6xp2Rdx8fe5icyapW+StaHBu4NE2tY0tXusT
sF5fnFSLq3htKaVWL7xnJwvZQfaTG2LUTmB3BpLgRjGRV6FmwiyMiUj2B5rm
C8qWU484SdJMu5HuffFnXZXj3Ji818bO265PZk666YypI4wCA7ZejZSH8wD2
Wpi1ot994FIp+3e0MviFrEI0iyBnyFtTFhYJ+4jMwg990nWdMuzQMaopGaH+
g21zmYcTUgAZy8hJDhVUxk25sijjVurT2cI0KokICZQGVmq9+XJYejOkJp2f
Z4+tptdUyo0JuOyp0Msx73o4hpVYMSrfJUzQRyEN+w7.IMXlALaEqgXqpBfo
9h63lBOM0Rd2L.SPUgInw.3D114ZBmndp0BBC78BHtwe12OJ6dDgYXAX1PxV
HcVr6XHODdDZ1.sliiidnqiOB8TKxaciauKu1B7bK168vdvE4Eulm7FdyM4f
LeQcbrY91ML0qC1p6nVnyZIbXKiS6AcbKoy6dbfKmS7AbjOny7AcnOfS8gcr
OnycIbvKiSdUbz2iy9Ac32uS+9c72uy+dC.PTP.cGHfXCQCGPP2AEzzjRSq4
speHq50sr+S2qAaVYWyEqKK5nl2X+5ahBo.avleqEe5Y1cY0ueK+8.5C6Any
ouUs1ROq08tNy7k+6upAFKeAOI7ECHjwWL3Sd13C9RV0+buLEjXlhwznr3v0
O.7PkXYF5Clx+drLEyogojGpp9GLkoPSwZRYJenoTionc+nc2CgSBiIaeHXj
4Pgyeb9vuxIYBCMMQgg.btB5C0kJbkm8RRCieazAHqOM7FHWIgu1l5luSzX1
DteOIHUHy4v+L3eMZNyzDNFzzgonfKzZXdbFjy.jlybAB6tiFymlnsfNr4kf
r46jImqALetBkBYMktrQ1nObNLcNGrmLSPY4tU+ckugYKZJmoTgw13C8kiLE
u.Mbu7EPO7EnLS4i6R.y+ErHpBmeXcyaa7IZ5OLdrEHA1ZZxwS9VwR1jzhNA
r8tKD7M5Y2jvXM7CiehylR.vV4YXkAv7Um6cfvah6yYKh3XMWC0kWz0Ru6cQ
3UJxN5XFskGRgv7Mi3h3f6hvCFZrVYgH4SZ46LOXTXENZXUpnw3a1Ay2UnJc
TM9k1UW9TFpC3Q4JqKqdlHdOfV8MdQ1FQZfUImMfyZW+HZR3g3ME7s7UePqM
Irkjj5ETtkU9R4xGoAFIudriOSEFeYS+WC1pw681FE5EjlTr.77DpXw2kKV1
kWsvjlghP+fTlAvpR54z0MJSi5BSYXEnLiNorv3s7coF3hcfi5rskCb3hNvy
lHuzi7toxFBSPSt9A+Mnz.AKu5RgYoDMir5mcgtfG55pyuPHlYsA3WKrLpsJ
DsC2tvxNBUwaHBo.aAyiFCAOd0EiZjJDc1hheAY0SWU90hKQgTXDpeFhuBAU
zW8hO.ApHddVfPEFfVmAYPnopH3hOBUQO19bL.QJN.uXrtCUU57hw3NTEKSB
hsn1awg8c7WsW5O5V.Gq1uJG83+luVvH9aNR8q3qBY9DI0MW7YaAUMrp9GfU
p7XMy66a01MqydEZD9JVAE7JVgj6UrJ+OFWGu9dkmbFfGbbz9DElnLzOQeFZ
p+d8U6Npszu+laZ3PnqIOCi4GtR.mhEzYNeA1DsNuyKx+yBQVT2HqkbRl57o
U28JJ72HIy78Fhl6K6TUIFcRhf4Z1.1ByXAtdk.4594mdLYmIdmnlO3TfcLW
yWmeDqgfvqWbeu2qp9l+ZNARz57WOr7M3zUIx9S+GsDp3rOIN6MCTUW+1BA4
laZodV3QH+X8vFrDu50mI42zvmT04EzYJ.27cOo90K1xsImc1Vop42IAfwNc
enec8.vaI9tuo8oxHdgZehNyLRbjVRDahRJJXabRvdtoYnM+7Gy4JVxtwVTP
tPJlBvkKSiuhMH2beJHk6N8SCasxWSHn3ctf3csf.vUBz63Q.UqMvvQ.sqrd
TAVaksiVqblnDY1HSG8xUUcPXI4fvbFGClRNFZk.vlo3BYvNDYMfbstJWMSi
bCIG4sxJbGIQ8rLvZmT0NRR5jNxvxNxxZHZl3aHEj5gxHwU7djYPmOaqK04m
FlH9r5YWsjxBxRrFxpdkGIL+O0uBx2I+4sDZieXQEtfRaS0dFsmAsU.wgy0f
vPEEsYaTHq5t0bxOPp.Ey1n.p.TLa7CfBV9P8YL.aw2Do7TNfAL89FWw249Y
uvmF4WMWjkZl35LBuaOVhhmRtj+bq6F4OyfG7XuUGf3Ikr3WAG6sf1G6sS2Y
76FeunencOTq6y5ZbGD1obT+hAr+XBVti52w9UOH+iDCu5WbiKoz10Njrfyv
3Bl6IEkqeIDXL54HyFN.DcW0+q5mGlhOmBE2erW0y+OX0OHR4kWg.JVh5h2c
mZC9rCXtsO5llF6s9PJ43+kz7LW9EW+CjvmZevJejR8CC1IlKTqoIOGFmJYa
K.JPG0seO+P19dqJGGc0p2kIHY1YsdAdoYZEE3zQSWUZzAZiJEy0uspEqQYl
p9GzgpBt+uvfeicBg5k91m8id1E8EzWk9q6h9nT6463.a8y8mDhNO9uo3l2d
JVkUJ+3SunBJmKuhiEdZeWIDX+MpS7GzwArtwoX1kMyDiVqZ6I+QE58ywqN+
jBFBXRxl5fx3f93PP+iCA8ONDzGSlkSH9ZXzxtlHbePEexLwRjYYj5osmYb7
tKiz2+MxaptvHlSABm+sWTlMJjt5Hb9mty1+YoPb9HR48NjtTfGpHy1E+dRK
7QwAFUyx8B1RdUTR5lkkBw7jm+9xkxbj9vIQn1jb3dE6YFNJY8lFJwZW+bay
k5e8YJ+n89wO2g5msXUhRkF9RhVRDM.DpmRo+l.gGUHqPcV5zgU91Rg.pjcj
oKQ.BBZ2OjhG+fprBx1Yaxl3D6S4SjDOw.1VWz4MQbNl17Mo+RRYcBvDWZYJ
+RXq.JwZScykbPqoIpueqDqTrnbWezpTKliJ8CTh9Adh8isDzCZBnGKI5G6I
neLjg+fmfNReg.NrLHG1XJ5IYvNqonizkTX3TEtw.YXRlSAIIQGoOA8CxbgD
6PKkvP8WlUQZrSROAkomlDtjLLo5JA0WM9Ysmqul3sNIS.7YClePljGLS0qf
17MPNeowXW0lL.yOYf5F.QmTOCsVHEL3R4.AhWpNRFtlybH0KcOC6WPkGcXi
Tbm0oMRscizZ2Nk1hSmcyTYS64+51+OvR.JNw
-----------end_max5_patcher-----------
```


