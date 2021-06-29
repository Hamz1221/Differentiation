<template>
    <div>
        <iv-visualisation :title="pageName" :vue_config="vue_config" :page_number="2">
            <template #hotspots>
              <iv-pane position="left" id="pane">
                  <iv-sidebar-content>
                    <iv-sidebar-section title="Theory">
                      <p>
                      Given some solid, how can we model sound waves moving through it?
                      </p>
                      <p>
                      Let us assume that this is a simple solid, made of identical atoms spaced evenly.
                      We know that atoms in a solid lattice are held together by binding forces, for example ionic, covalent and metallic bonds.
                      The Mie potential shown on the right is generally a good model for binding forces in solids.
                      </p>
                      <p>
                      Let us model the binding forces using springs. 
                      We model all atoms as connected to only their nearest neighbours by identical springs.
                      This model is accurate in the small displacement limit, that is the low temperature limit.
                      </p>
                    </iv-sidebar-section>
                    <iv-sidebar-section title="Explanation" icon="question" theme="Lime" highlight>
                        Let's explore this model. 
                      We will start considering the simple case of a one dimensional lattice, building up the theory. 
                      Here we will develop the concept of the first Brillouin Zone and how energy moves through the solid in the form of waves.
                      Then we will look at a two dimensional lattice and consider transverse and longitudinal waves passing through the solid.
                      We will continue to three dimensional solids for completeness.
                    </iv-sidebar-section>
                  </iv-sidebar-content>
               </iv-pane>

                            <iv-fixed-hotspot position="topleft" title="Equation" style="z-index:2; width:0px; height:0px" transparent>
                                  <div style="border-top:200px;">
                                    <img src="../assets/limitEquation.svg" style="position: relative; left:600px; top: 100px; -webkit-filter: invert(1); filter: invert(1);"/>
                                    <p style="position: relative; left:870px; top:45px; -webkit-filter: invert(1); filter: invert(1);">{{derivDisp}}</p>
                                  </div>
                            </iv-fixed-hotspot>

                            <iv-toggle-hotspot position="right" title="Sidebar" style="z-index:2;">
                                <div class="slidecontainer" style="float:right;">
                                  Function: 
                                  <select id="function" style="width:188px; padding:0px; margin: 0px;">
                                    <option value="sin">Sin(x)</option>
                                    <option value="exp">Exponential Decay</option>
                                    <option value="tan">Tan(x)</option>
                                    <option value="gauss">Gaussian</option>
                                    <option value="parab">Parabola (2nd Order Polynomial)</option>
                                    <!-- <option value="parabStep">Parabola with Step Function</option> -->
                                    <option value="poly">Polynomial (6th Order)</option>
                                  </select>
                                  <br>
                                  
                                  <button style="margin-top: 15px;" type="button" id="animButton">Plot Derivative</button><br>
                                  <input type="checkbox" id="checkbox" name="check" value="display" style="margin-top: 15px;">
                                  <label for="checkbox"> Show link</label>                                  
                                  <!-- Delta x:
                                  <input type="range" min="0.0001" max="100" value="25" class="slider" id="deltaX" name="deltax" step="0.0001" style="width:188px;margin-top:19px;margin-bottom:14px;"> -->
                                  
                                  <!-- <iv-equation-box equation="f(x)=lim_{\delta x \to 0} \frac{f(x - \delta x)}{\delta x} = \qquad">hi</iv-equation-box> -->

                                  


                                </div>
                            </iv-toggle-hotspot>
                        </template>




            <body style="margin:0px; padding:0px; width: 100%;">



<svg
   xmlns:ns0="http://www.iki.fi/pav/software/textext/"
   xmlns:dc="http://purl.org/dc/elements/1.1/"
   xmlns:cc="http://creativecommons.org/ns#"
   xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
   xmlns:svg="http://www.w3.org/2000/svg"
   xmlns="http://www.w3.org/2000/svg"
   xmlns:xlink="http://www.w3.org/1999/xlink"
   version="1.1"
   id="root"
   height="850"
   width="100%">
   <!--when I change height to 100%, the graphs are cut off- not sure why-->
   <defs>
      <g id = "derivColourmask">
         <rect  x="0" y="297.57214" height="200" width="570" fill="green"   stroke="none" />
         <rect x="0" y="497.57214" height="200" width="570" fill="red" stroke="none"/>
         <rect x="0" y="496.57214" height="2" width="570" fill="white" stroke="none"/>
     </g>
     <g id = "sinColourmask">
         <rect  x="55.123835" y="0" height="875" width="43" fill="green"   stroke="none" />
         <rect x="98.123835" y="0" height="875" width="85" fill="red" stroke="none"/>
         <rect  x="97.123835" y="0" height="875" width="2" fill="white"   stroke="none" />
         <rect x="183.123835" y="0" height="875" width="86" fill="green" stroke="none"/>
         <rect  x="181.8" y="0" height="875" width="2" fill="white"   stroke="none" />
         <rect x="269" y="0" height="875" width="85.8" fill="red" stroke="none"/>
         <rect  x="267.7" y="0" height="875" width="2" fill="white"   stroke="none" />
         <rect x="355.123835" y="0" height="875" width="85" fill="green" stroke="none"/>
         <rect  x="352.9" y="0" height="875" width="2" fill="white"   stroke="none" />
         <rect x="440.123835" y="0" height="875" width="85" fill="red" stroke="none"/>
         <rect  x="438.5" y="0" height="875" width="2" fill="white"   stroke="none" />
         <rect x="525.123835" y="0" height="875" width="45" fill="green" stroke="none"/>
         <rect  x="523.7" y="0" height="875" width="2" fill="white"   stroke="none" />
      </g>
      <g id = "expColourmask">
         <rect  x="55.123835" y="0" height="875" width="570" fill="red"   stroke="none" />
      </g>
      <g id = "tanColourmask">
         <rect  x="55.123835" y="0" height="875" width="570" fill="green"   stroke="none" />
      </g>
      <g id = "gaussColourmask">
         <rect  x="55.123835" y="0" height="875" width="256" fill="green"   stroke="none" />
         <rect  x="311.123835" y="0" height="875" width="256" fill="red"   stroke="none" />
         <rect  x="310" y="0" height="875" width="2" fill="white"   stroke="none" />
      </g>
      <g id = "parabColourmask">
         <rect  x="55.123835" y="0" height="875" width="256" fill="red"   stroke="none" />
         <rect  x="311.123835" y="0" height="875" width="256" fill="green"   stroke="none" />
         <rect  x="310" y="0" height="875" width="2" fill="white"   stroke="none" />
      </g>
      <g id = "polyColourmask">
         <rect  x="55.123835" y="0" height="875" width="64" fill="red"   stroke="none" />
         <rect  x="119.123835" y="0" height="875" width="128" fill="green"   stroke="none" />
         <rect  x="247.123835" y="0" height="875" width="2" fill="white"   stroke="none" />
         <rect  x="118" y="0" height="875" width="2" fill="white"   stroke="none" />
         <rect  x="248.123835" y="0" height="875" width="191" fill="green"   stroke="none" />
         <rect  x="439.123835" y="0" height="875" width="64" fill="red"   stroke="none" />
         <rect  x="438" y="0" height="875" width="2" fill="white"   stroke="none" />
         <rect  x="503.123835" y="0" height="875" width="67" fill="green"   stroke="none" />
         <rect  x="503" y="0" height="875" width="2" fill="white"   stroke="none" />
      </g>
   </defs>
   <filter id="deriv" x="0" y="0" width="570" height="875" filterUnits="userSpaceOnUse">
      <feImage xlink:href="#derivColourmask" result="mask1"/>
       <feComposite in2="SourceGraphic" in="mask1" operator="in" />
   </filter>
   <filter id="func" x="0" y="0" width="570" height="875" filterUnits="userSpaceOnUse">
      <feImage id="funcSRC" xlink:href="#sinColourmask" result="mask1"/>
       <feComposite in2="SourceGraphic" in="mask1" operator="in" />
   </filter>


   <!-- h=700, w-570 -->
   <!-- change height of above to vary blue bit, so 2 graphs can be included (line 22 and 139)-->
  <defs
     id="defs4">
    <marker
       style="overflow:visible"
       id="marker9114"
       refX="0.0"
       refY="0.0"
       orient="auto">
      <path 
         transform="scale(0.4) translate(7.4, 1)"
         style="fill-rule:evenodd;stroke:black;stroke-width:1pt;stroke-opacity:1;fill:#5DFF33;fill-opacity:1"
         d="M -2.5,-1.0 C -2.5,1.7600000 -4.7400000,4.0 -7.5,4.0 C -10.260000,4.0 -12.5,1.7600000 -12.5,-1.0 C -12.5,-3.7600000 -10.260000,-6.0 -7.5,-6.0 C -4.7400000,-6.0 -2.5,-3.7600000 -2.5,-1.0 z "
         id="path9112" /> <!-- draws circles-->
    </marker>
    <marker
       style="overflow:visible"
       id="marker7900"
       refX="0.0"
       refY="0.0"
       orient="auto">
      <path
         transform="scale(0.4)"
         style="fill-rule:evenodd;stroke:white;stroke-width:1pt;stroke-opacity:1;fill:white;fill-opacity:1"
         d="M 5.77,0.0 L -2.88,5.0 L -2.88,-5.0 L 5.77,0.0 z "
         id="path7898" /> <!-- draws axes... or is it line between -->
    </marker>
    <marker
       style="overflow:visible"
       id="TriangleOutM"
       refX="0.0"
       refY="0.0"
       orient="auto">
      <path
         transform="scale(0.4)"
         style="fill-rule:evenodd;stroke:white;stroke-width:1pt;stroke-opacity:1;fill:white;fill-opacity:1"
         d="M 5.77,0.0 L -2.88,5.0 L -2.88,-5.0 L 5.77,0.0 z "
         id="path7713" />
         <!-- The white arrow on the x-axis -->
    </marker>
    <!-- <radialGradient
       gradientUnits="userSpaceOnUse"
       gradientTransform="matrix(-0.65523826,0,0,-0.6247619,1172.0929,131.92585)"
       r="280"
       fy="105.07805"
       fx="447.40897"
       cy="105.07805"
       cx="447.40897"
       id="radialGradient4581"
       xlink:href="#linearGradient4579" /> -->
    <linearGradient
       id="linearGradient4579">
      <stop
         id="stop4575"
         offset="0"
         style="stop-color:#7aaed7;stop-opacity:1" />
         <!-- Radial colour at the top of the viewing box -->
      <stop
         id="stop4577"
         offset="1"
         style="stop-color:#466589;stop-opacity:1" />
         <!-- Radial colour at the bottom of the viewing box -->
    </linearGradient>
    <marker
       orient="auto"
       refY="0"
       refX="0"
       id="marker14780"
       style="overflow:visible">
      <path
         id="path14778"
         d="m -2.5,-1 c 0,2.76 -2.24,5 -5,5 -2.76,0 -5,-2.24 -5,-5 0,-2.76 2.24,-5 5,-5 2.76,0 5,2.24 5,5 z"
         style="fill:#7aaed7;fill-opacity:1;fill-rule:evenodd;stroke:none;stroke-width:1.00000003pt;stroke-opacity:1"
         transform="matrix(0.2,0,0,0.2,1.48,0.2)" />
    </marker>
    <marker
       orient="auto"
       refY="0"
       refX="0"
       id="marker15030"
       style="overflow:visible">
      <path
         id="path15028"
         d="M 5.77,0 -2.88,5 V -5 Z"
         style="fill:#466589;fill-opacity:1;fill-rule:evenodd;stroke:none;stroke-width:1.00000003pt;stroke-opacity:1"
         transform="scale(0.4)" />
    </marker>
    <radialGradient
       gradientUnits="userSpaceOnUse"
       gradientTransform="matrix(-1.7857144,-1.0178571,1.0178573,-1.7857143,301.27202,466.26987)"
       r="550"
       fy="105.078"
       fx="56.057446"
       cy="105.078"
       cx="56.057446"
       id="radialGradient4581-1"
       xlink:href="#linearGradient4579" />
    <clipPath
       id="clipPath19347"
       clipPathUnits="userSpaceOnUse">
      <rect
         style="color:white;display:inline;overflow:visible;visibility:visible;opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:nonzero;stroke:white;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;paint-order:stroke fill markers;enable-background:accumulate"
         id="rect19349"
         width="528"
         height="394"
         x="47.123837"
         y="297.57214" />
    </clipPath>
    <clipPath
      id="reveal">
      <rect id="rect" width="0" height="10000" x="55.123835"/>
   </clipPath>
  </defs>
  <g
     transform="translate(-23.123835,-271.57211)"
     id="layer1">
    <rect
       style="color:white;display:inline;overflow:hidden;visibility:visible;opacity:1;vector-effect:none;fill:url(#radialGradient4581-1);fill-opacity:1;fill-rule:nonzero;stroke:none;stroke-width:0.99999994;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;paint-order:stroke fill markers;enable-background:accumulate"
       id="rect4573-0"
       width="100%"
       height="10000"
       x="23.123835"
       y="221.57211" />
    <!--<rect
       transform="translate(23.123835,221.57211)"
       y="0"
       x="0"
       height="0"
       width="0"
       id="rect7177"
       style="color:white;display:inline;overflow:visible;visibility:visible;opacity:1;vector-effect:none;fill:url(#radialGradient4581);fill-opacity:1;fill-rule:nonzero;stroke:none;stroke-width:1;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-start:url(#marker14780);marker-end:url(#marker15030);paint-order:stroke fill markers;enable-background:accumulate" />-->
    <!-- <rect
       style="fill: #7aaed7; stroke: white;"
       id="right-side-pane"
       x="625"
       y="300"
       width="400"
       height="380"
       pathLength="2800"
       transform="translate(0,-2)"/> -->
    <g
       clip-path="url(#clipPath19347)"
       id="graph">
      <rect
         style="fill: transparent;"
         width="528"
         height="800"
         x="47.123837"
         y="200.57214" />
      <g
         id="g9544" transform="translate(0,0)">
        <path
           id="yAxis"
           d="m 55.123835,689.57214 v -384"
           style="opacity:1;vector-effect:none;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-end:url(#marker7900);paint-order:stroke fill markers" />
        <path
           id="xAxis"
           d="M 55.123835,497.57214 H 567.12383"
           style="opacity:1;vector-effect:none;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-end:url(#TriangleOutM);paint-order:stroke fill markers" />
      </g>
      <path
         style="opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:evenodd;stroke:#afdb85;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;paint-order:stroke fill markers"
         d="M 55.123835,497.57214 H 567.12383"
         id="fx"
         filter="url(#func)"/>

      <line
         x1="-1000" y1="497.57214" x2="1300" y2="497.57214" transform="translate(0,0) rotate(0)" id="lineExt" style="stroke:black" stroke-width="2"/>
      <path
         style="opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-start:url(#marker9114);marker-end:url(#marker9114);paint-order:stroke fill markers"
         d="m 55.123835,497.57214 v 0"
         id="blob" /> <!-- line between two blobs-->
       <path
         style="opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:evenodd;stroke:black;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-start:url(#marker9114);marker-end:url(#marker9114);paint-order:stroke fill markers"
         d="m 55.123835,497.57214 v 0"
         id="blob2" /> <!-- line between two of the blobs-->
      <!-- <circle cx="55.123835" cy="497.57214" r="10"/> The Origin of the axises -->
    </g>
    <g
       style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0.5;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
       ns0:preamble="/home/afp11/.config/inkscape/extensions/default_packages.tex"
       ns0:text="\\[\nx\n\\]"
       word-spacing="normal"
       letter-spacing="normal"
       font-size-adjust="none"
       font-stretch="normal"
       font-weight="normal"
       font-variant="normal"
       font-style="normal"
       stroke-miterlimit="10.433"
       xml:space="preserve"
       transform="matrix(2.4000001,0,0,-2.4,-166.46648,2191.4404)"
       id="content">
       <path
         style="fill:white;stroke-width:0"
         id="path10149"
         d="m 306.11,698.17 v 0.03 l 0.01,0.03 0.01,0.03 0.01,0.03 0.01,0.04 0.01,0.04 0.01,0.05 0.02,0.04 0.01,0.05 0.02,0.05 0.02,0.04 0.02,0.05 0.02,0.05 0.03,0.05 0.02,0.05 0.03,0.05 0.03,0.05 0.03,0.05 0.04,0.04 0.03,0.05 0.04,0.04 0.04,0.04 0.04,0.04 0.04,0.04 0.05,0.03 0.05,0.03 0.03,0.01 0.02,0.01 0.03,0.01 0.02,0.01 0.03,0.01 0.03,0.01 0.03,0.01 h 0.03 l 0.03,0.01 h 0.03 0.03 0.04 c 0.04,0 0.28,0 0.49,-0.13 -0.28,-0.05 -0.48,-0.3 -0.48,-0.53 0,-0.16 0.12,-0.35 0.38,-0.35 0.22,0 0.54,0.18 0.54,0.58 0,0.51 -0.59,0.65 -0.92,0.65 -0.58,0 -0.93,-0.53 -1.05,-0.75 -0.25,0.65 -0.79,0.75 -1.08,0.75 -1.04,0 -1.6,-1.28 -1.6,-1.53 0,-0.1 0.1,-0.1 0.11,-0.1 0.09,0 0.12,0.02 0.13,0.11 0.34,1.05 1,1.3 1.34,1.3 0.19,0 0.54,-0.09 0.54,-0.66 0,-0.31 -0.17,-0.98 -0.54,-2.37 -0.16,-0.61 -0.51,-1.03 -0.95,-1.03 -0.06,0 -0.29,0 -0.49,0.13 0.24,0.05 0.46,0.26 0.46,0.54 0,0.26 -0.22,0.34 -0.37,0.34 -0.29,0 -0.54,-0.26 -0.54,-0.57 0,-0.46 0.5,-0.66 0.93,-0.66 0.66,0 1.02,0.7 1.05,0.76 0.12,-0.37 0.48,-0.76 1.08,-0.76 1.02,0 1.59,1.28 1.59,1.53 0,0.1 -0.09,0.1 -0.12,0.1 -0.09,0 -0.11,-0.04 -0.13,-0.11 -0.33,-1.06 -1,-1.3 -1.32,-1.3 -0.39,0 -0.55,0.32 -0.55,0.65 0,0.22 0.06,0.44 0.17,0.88 z" />
      </g> <!-- The 'x' on the x-axis -->
      <g
       id="g10296"
       transform="matrix(2.4000001,0,0,-2.4,-641.45589,1972.3464)"
       xml:space="preserve"
       stroke-miterlimit="10.433"
       font-style="normal"
       font-variant="normal"
       font-weight="normal"
       font-stretch="normal"
       font-size-adjust="none"
       letter-spacing="normal"
       word-spacing="normal"
       ns0:text="\\[\nf(x)\n\\]"
       ns0:preamble="/home/afp11/.config/inkscape/extensions/default_packages.tex"
       style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0.5;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1">
       <path
         d="m 299.59,699.14 h 0.86 c 0.19,0 0.29,0 0.29,0.2 0,0.11 -0.1,0.11 -0.26,0.11 h -0.83 l 0.21,1.13 c 0.04,0.21 0.18,0.92 0.24,1.04 0.09,0.19 0.26,0.34 0.47,0.34 0.04,0 0.29,0 0.48,-0.18 -0.44,-0.04 -0.53,-0.39 -0.53,-0.54 0,-0.23 0.18,-0.35 0.36,-0.35 0.26,0 0.55,0.22 0.55,0.6 0,0.46 -0.46,0.68 -0.86,0.68 -0.34,0 -0.97,-0.18 -1.27,-1.16 -0.06,-0.21 -0.09,-0.31 -0.33,-1.56 h -0.69 c -0.19,0 -0.3,0 -0.3,-0.19 0,-0.12 0.09,-0.12 0.28,-0.12 h 0.66 l -0.75,-3.92 c -0.18,-0.96 -0.35,-1.87 -0.87,-1.87 -0.04,0 -0.28,0 -0.47,0.18 0.45,0.03 0.54,0.39 0.54,0.54 0,0.23 -0.18,0.34 -0.36,0.34 -0.26,0 -0.55,-0.21 -0.55,-0.59 0,-0.45 0.43,-0.69 0.84,-0.69 0.55,0 0.95,0.59 1.13,0.97 0.32,0.62 0.55,1.82 0.56,1.89 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10288" />
         <!-- the 'f' in 'f(x)' on the y-axis -->
         <path
         d="m 305.18,692.79 v 0 0.01 0 0 0.01 0 0 l -0.01,0.01 v 0 0 0.01 h -0.01 v 0.01 0 l -0.01,0.01 v 0.01 h -0.01 v 0.01 h -0.01 v 0.01 0 l -0.01,0.01 v 0 0 l -0.01,0.01 v 0 l -0.01,0.01 v 0 l -0.01,0.01 v 0 l -0.01,0.01 v 0.01 h -0.01 v 0.01 h -0.01 l -0.01,0.01 v 0.01 h -0.01 l -0.01,0.01 -0.01,0.01 V 693 h -0.01 c -1.25,1.26 -1.57,3.13 -1.57,4.65 0,1.73 0.38,3.46 1.61,4.7 0.13,0.12 0.13,0.14 0.13,0.17 0,0.07 -0.04,0.1 -0.1,0.1 -0.1,0 -1,-0.67 -1.59,-1.94 -0.51,-1.09 -0.63,-2.19 -0.63,-3.03 0,-0.77 0.12,-1.97 0.66,-3.1 0.6,-1.22 1.46,-1.86 1.56,-1.86 0.06,0 0.1,0.03 0.1,0.1 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10290" />
         <!-- The '(' in 'f(x)' on the y-axis -->
         <path
         d="m 309.08,698.17 0.01,0.03 0.01,0.03 v 0.03 l 0.01,0.03 0.01,0.04 0.02,0.04 0.01,0.05 0.01,0.04 0.02,0.05 0.02,0.05 0.02,0.04 0.02,0.05 0.02,0.05 0.02,0.05 0.03,0.05 0.03,0.05 0.03,0.05 0.03,0.05 0.03,0.04 0.04,0.05 0.03,0.04 0.04,0.04 0.05,0.04 0.04,0.04 0.05,0.03 0.04,0.03 0.03,0.01 0.03,0.01 0.02,0.01 0.03,0.01 0.03,0.01 0.03,0.01 0.02,0.01 h 0.03 l 0.03,0.01 h 0.04 0.03 0.03 c 0.05,0 0.29,0 0.5,-0.13 -0.28,-0.05 -0.48,-0.3 -0.48,-0.53 0,-0.16 0.11,-0.35 0.38,-0.35 0.22,0 0.54,0.18 0.54,0.58 0,0.51 -0.59,0.65 -0.93,0.65 -0.58,0 -0.93,-0.53 -1.05,-0.75 -0.25,0.65 -0.79,0.75 -1.07,0.75 -1.04,0 -1.61,-1.28 -1.61,-1.53 0,-0.1 0.1,-0.1 0.12,-0.1 0.08,0 0.11,0.02 0.13,0.11 0.34,1.05 1,1.3 1.34,1.3 0.18,0 0.53,-0.09 0.53,-0.66 0,-0.31 -0.17,-0.98 -0.53,-2.37 -0.16,-0.61 -0.51,-1.03 -0.95,-1.03 -0.06,0 -0.29,0 -0.5,0.13 0.25,0.05 0.47,0.26 0.47,0.54 0,0.26 -0.22,0.34 -0.37,0.34 -0.3,0 -0.55,-0.26 -0.55,-0.57 0,-0.46 0.5,-0.66 0.94,-0.66 0.66,0 1.02,0.7 1.05,0.76 0.11,-0.37 0.47,-0.76 1.07,-0.76 1.03,0 1.6,1.28 1.6,1.53 0,0.1 -0.09,0.1 -0.12,0.1 -0.09,0 -0.11,-0.04 -0.13,-0.11 -0.33,-1.06 -1.01,-1.3 -1.33,-1.3 -0.39,0 -0.55,0.32 -0.55,0.65 0,0.22 0.06,0.44 0.17,0.88 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10292" />
         <!-- The 'x' in 'f(x)' on the y-axis -->
         <path
         d="m 314.33,697.65 v 0.08 0.07 l -0.01,0.08 v 0.08 l -0.01,0.17 -0.01,0.18 -0.01,0.18 -0.03,0.19 -0.02,0.19 -0.04,0.2 -0.03,0.21 -0.05,0.2 -0.05,0.21 -0.07,0.21 -0.07,0.22 -0.07,0.21 -0.05,0.11 -0.04,0.1 -0.05,0.11 -0.05,0.1 c -0.6,1.22 -1.46,1.87 -1.56,1.87 -0.06,0 -0.1,-0.04 -0.1,-0.1 0,-0.03 0,-0.05 0.19,-0.23 0.98,-0.98 1.55,-2.56 1.55,-4.64 0,-1.69 -0.37,-3.44 -1.61,-4.69 -0.13,-0.12 -0.13,-0.14 -0.13,-0.17 0,-0.06 0.04,-0.1 0.1,-0.1 0.1,0 1,0.67 1.59,1.93 0.51,1.1 0.63,2.2 0.63,3.03 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10294" />
         <!-- The ')' in 'f(x)' on the y-axis -->
      </g>
      <!-- <g transform="translate(0,80)">
      <text
       id="text18342"
       y="257.57214"
       x="55.123837"
       style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;font-size:16px;line-height:125%;font-family:Helvetica;-inkscape-font-specification:Helvetica;text-align:start;letter-spacing:0px;word-spacing:0px;text-anchor:start;fill:white;fill-opacity:1;stroke:none;stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1;"
       xml:space="preserve">
       <tspan
         style="font-size:18.66666603px;text-align:start;text-anchor:start;fill:white;user-select:none;-moz-user-select: none;"
         y="272.57214"
         x="660.123837"
         id="tspan18340">Function</tspan>
      </text> -->
      <!-- 'Function' next to the function select box-->
      <!-- <foreignObject
       y="255.90814"
       x="760.80826"
       height="32"
       width="192"
       style="overflow:visible;"
       id="foFunction">
       <select id="function" style="width:188px; padding:0px; margin: 0px;">
        <option value="sin">Sin(x)</option>
        <option value="exp">Exponential Decay</option>
        <option value="tan">Tan(x)</option>
        <option value="gauss">Gaussian</option>
        <option value="parab">Parabola (2nd Order Polynomial)</option> -->
        <!-- <option value="parabStep">Parabola with Step Function</option> -->
        <!-- <option value="poly">Polynomial (6th Order)</option>
       </select>
       <div class="slidecontainer">
       </div>
       <button style="margin-top: 15px;" type="button" id="animButton">Plot Derivative</button><br>
       <input type="checkbox" id="checkbox" name="check" value="display" style="margin-top: 15px;">
       <label for="checkbox"> Show link</label>
      </foreignObject>
      </g> -->
    <!-- The function select box -->
    
  </g>
  <g
     transform="translate(-23.123835,200)"
     id="layer2">
    <rect
       style="color:white;display:inline;overflow:visible;visibility:hidden;opacity:1;vector-effect:none;fill:url(#radialGradient4581-1);fill-opacity:1;fill-rule:nonzero;stroke:none;stroke-width:0.99999994;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;paint-order:stroke fill markers;enable-background:accumulate"
       id="rect4573-0-1"
       width="570"
       height="400"
       x="23.123835"
       y="222" />-->
       <!--The above section creates separate rectangles for the graphs-->
    <rect
       transform="translate(23.123835,221.57211)"
       y="0"
       x="0"
       height="0"
       width="0"
       id="rect7177-1"
       style="color:white;display:inline;overflow:visible;visibility:visible;opacity:1;vector-effect:none;fill:url(#radialGradient4581);fill-opacity:1;fill-rule:nonzero;stroke:none;stroke-width:1;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-start:url(#marker14780);marker-end:url(#marker15030);paint-order:stroke fill markers;enable-background:accumulate" />
    <g
       clip-path="url(#clipPath19347)"
       id="graph1"
       transform="translate(0,-70)">
      <rect
         style="fill: transparent;"
         width="528"
         height="400"
         x="47.123837"
         y="297.57214" />
      <g
         id="g9544-1">
        <path
           id="yAxis-1"
           d="m 55.123835,689.57214 v -384"
           style="opacity:1;vector-effect:none;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-end:url(#marker7900);paint-order:stroke fill markers" />
        <path
           id="xAxis-1"
           d="M 55.123835,497.57214 H 567.12383"
           style="opacity:1;vector-effect:none;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-end:url(#TriangleOutM);paint-order:stroke fill markers" />
      </g>
      <path
         style="opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:evenodd;stroke:#afdb85;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-opacity:1;marker:none;paint-order:stroke fill markers"
         d="M 55.123835,497.57214 H 567.12383"
         id="fx-1" 
         visibility="visible"
         clip-path="url(#reveal)"
         filter="url(#deriv)"/>   
    </g>
    <path marker-start="url(#marker9114)" d="M 361.6 377 L 361.5 350" clip-path="url(#reveal)" id="discont" visibility="hidden"></path>
    <g
       style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0.5;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
       ns0:preamble="/home/afp11/.config/inkscape/extensions/default_packages.tex"
       ns0:text="\\[\nx\n\\]"
       word-spacing="normal"
       letter-spacing="normal"
       font-size-adjust="none"
       font-stretch="normal"
       font-weight="normal"
       font-variant="normal"
       font-style="normal"
       stroke-miterlimit="10.433"
       xml:space="preserve"
       transform="matrix(2.4000001,0,0,-2.4,-166.46648,2191.4404) translate(0,28)"
       id="content-1">
       <path
         style="fill:white;stroke-width:0"
         id="path10149-1"
         d="m 306.11,698.17 v 0.03 l 0.01,0.03 0.01,0.03 0.01,0.03 0.01,0.04 0.01,0.04 0.01,0.05 0.02,0.04 0.01,0.05 0.02,0.05 0.02,0.04 0.02,0.05 0.02,0.05 0.03,0.05 0.02,0.05 0.03,0.05 0.03,0.05 0.03,0.05 0.04,0.04 0.03,0.05 0.04,0.04 0.04,0.04 0.04,0.04 0.04,0.04 0.05,0.03 0.05,0.03 0.03,0.01 0.02,0.01 0.03,0.01 0.02,0.01 0.03,0.01 0.03,0.01 0.03,0.01 h 0.03 l 0.03,0.01 h 0.03 0.03 0.04 c 0.04,0 0.28,0 0.49,-0.13 -0.28,-0.05 -0.48,-0.3 -0.48,-0.53 0,-0.16 0.12,-0.35 0.38,-0.35 0.22,0 0.54,0.18 0.54,0.58 0,0.51 -0.59,0.65 -0.92,0.65 -0.58,0 -0.93,-0.53 -1.05,-0.75 -0.25,0.65 -0.79,0.75 -1.08,0.75 -1.04,0 -1.6,-1.28 -1.6,-1.53 0,-0.1 0.1,-0.1 0.11,-0.1 0.09,0 0.12,0.02 0.13,0.11 0.34,1.05 1,1.3 1.34,1.3 0.19,0 0.54,-0.09 0.54,-0.66 0,-0.31 -0.17,-0.98 -0.54,-2.37 -0.16,-0.61 -0.51,-1.03 -0.95,-1.03 -0.06,0 -0.29,0 -0.49,0.13 0.24,0.05 0.46,0.26 0.46,0.54 0,0.26 -0.22,0.34 -0.37,0.34 -0.29,0 -0.54,-0.26 -0.54,-0.57 0,-0.46 0.5,-0.66 0.93,-0.66 0.66,0 1.02,0.7 1.05,0.76 0.12,-0.37 0.48,-0.76 1.08,-0.76 1.02,0 1.59,1.28 1.59,1.53 0,0.1 -0.09,0.1 -0.12,0.1 -0.09,0 -0.11,-0.04 -0.13,-0.11 -0.33,-1.06 -1,-1.3 -1.32,-1.3 -0.39,0 -0.55,0.32 -0.55,0.65 0,0.22 0.06,0.44 0.17,0.88 z" />
      </g> <!-- The 'x' on the x-axis -->
      <g
       id="g10296-1"
       transform="matrix(2.4000001,0,0,-2.4,-641.45589,1972.3464) translate(0,20)"
       xml:space="preserve"
       stroke-miterlimit="10.433"
       font-style="normal"
       font-variant="normal"
       font-weight="normal"
       font-stretch="normal"
       font-size-adjust="none"
       letter-spacing="normal"
       word-spacing="normal"
       ns0:text="\\[\nf(x)\n\\]"
       ns0:preamble="/home/afp11/.config/inkscape/extensions/default_packages.tex"
       style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0.5;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1">
       <path
         d="m 299.59,699.14 h 0.86 c 0.19,0 0.29,0 0.29,0.2 0,0.11 -0.1,0.11 -0.26,0.11 h -0.83 l 0.21,1.13 c 0.04,0.21 0.18,0.92 0.24,1.04 0.09,0.19 0.26,0.34 0.47,0.34 0.04,0 0.29,0 0.48,-0.18 -0.44,-0.04 -0.53,-0.39 -0.53,-0.54 0,-0.23 0.18,-0.35 0.36,-0.35 0.26,0 0.55,0.22 0.55,0.6 0,0.46 -0.46,0.68 -0.86,0.68 -0.34,0 -0.97,-0.18 -1.27,-1.16 -0.06,-0.21 -0.09,-0.31 -0.33,-1.56 h -0.69 c -0.19,0 -0.3,0 -0.3,-0.19 0,-0.12 0.09,-0.12 0.28,-0.12 h 0.66 l -0.75,-3.92 c -0.18,-0.96 -0.35,-1.87 -0.87,-1.87 -0.04,0 -0.28,0 -0.47,0.18 0.45,0.03 0.54,0.39 0.54,0.54 0,0.23 -0.18,0.34 -0.36,0.34 -0.26,0 -0.55,-0.21 -0.55,-0.59 0,-0.45 0.43,-0.69 0.84,-0.69 0.55,0 0.95,0.59 1.13,0.97 0.32,0.62 0.55,1.82 0.56,1.89 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10288-1" />
         <!-- the 'f' in 'f(x)' on the y-axis -->

        <path
         d="m 301.59,700.14 l 1.5, 3 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0.5;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10288-1" />
         <!-- the ''' in 'f'(x)' -->
       <path
         d="m 305.18,692.79 v 0 0.01 0 0 0.01 0 0 l -0.01,0.01 v 0 0 0.01 h -0.01 v 0.01 0 l -0.01,0.01 v 0.01 h -0.01 v 0.01 h -0.01 v 0.01 0 l -0.01,0.01 v 0 0 l -0.01,0.01 v 0 l -0.01,0.01 v 0 l -0.01,0.01 v 0 l -0.01,0.01 v 0.01 h -0.01 v 0.01 h -0.01 l -0.01,0.01 v 0.01 h -0.01 l -0.01,0.01 -0.01,0.01 V 693 h -0.01 c -1.25,1.26 -1.57,3.13 -1.57,4.65 0,1.73 0.38,3.46 1.61,4.7 0.13,0.12 0.13,0.14 0.13,0.17 0,0.07 -0.04,0.1 -0.1,0.1 -0.1,0 -1,-0.67 -1.59,-1.94 -0.51,-1.09 -0.63,-2.19 -0.63,-3.03 0,-0.77 0.12,-1.97 0.66,-3.1 0.6,-1.22 1.46,-1.86 1.56,-1.86 0.06,0 0.1,0.03 0.1,0.1 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10290-1" />
         <!-- The '(' in 'f(x)' on the y-axis -->
         <path
         d="m 309.08,698.17 0.01,0.03 0.01,0.03 v 0.03 l 0.01,0.03 0.01,0.04 0.02,0.04 0.01,0.05 0.01,0.04 0.02,0.05 0.02,0.05 0.02,0.04 0.02,0.05 0.02,0.05 0.02,0.05 0.03,0.05 0.03,0.05 0.03,0.05 0.03,0.05 0.03,0.04 0.04,0.05 0.03,0.04 0.04,0.04 0.05,0.04 0.04,0.04 0.05,0.03 0.04,0.03 0.03,0.01 0.03,0.01 0.02,0.01 0.03,0.01 0.03,0.01 0.03,0.01 0.02,0.01 h 0.03 l 0.03,0.01 h 0.04 0.03 0.03 c 0.05,0 0.29,0 0.5,-0.13 -0.28,-0.05 -0.48,-0.3 -0.48,-0.53 0,-0.16 0.11,-0.35 0.38,-0.35 0.22,0 0.54,0.18 0.54,0.58 0,0.51 -0.59,0.65 -0.93,0.65 -0.58,0 -0.93,-0.53 -1.05,-0.75 -0.25,0.65 -0.79,0.75 -1.07,0.75 -1.04,0 -1.61,-1.28 -1.61,-1.53 0,-0.1 0.1,-0.1 0.12,-0.1 0.08,0 0.11,0.02 0.13,0.11 0.34,1.05 1,1.3 1.34,1.3 0.18,0 0.53,-0.09 0.53,-0.66 0,-0.31 -0.17,-0.98 -0.53,-2.37 -0.16,-0.61 -0.51,-1.03 -0.95,-1.03 -0.06,0 -0.29,0 -0.5,0.13 0.25,0.05 0.47,0.26 0.47,0.54 0,0.26 -0.22,0.34 -0.37,0.34 -0.3,0 -0.55,-0.26 -0.55,-0.57 0,-0.46 0.5,-0.66 0.94,-0.66 0.66,0 1.02,0.7 1.05,0.76 0.11,-0.37 0.47,-0.76 1.07,-0.76 1.03,0 1.6,1.28 1.6,1.53 0,0.1 -0.09,0.1 -0.12,0.1 -0.09,0 -0.11,-0.04 -0.13,-0.11 -0.33,-1.06 -1.01,-1.3 -1.33,-1.3 -0.39,0 -0.55,0.32 -0.55,0.65 0,0.22 0.06,0.44 0.17,0.88 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10292-1" />
         <!-- The 'x' in 'f(x)' on the y-axis -->
         <path
         d="m 314.33,697.65 v 0.08 0.07 l -0.01,0.08 v 0.08 l -0.01,0.17 -0.01,0.18 -0.01,0.18 -0.03,0.19 -0.02,0.19 -0.04,0.2 -0.03,0.21 -0.05,0.2 -0.05,0.21 -0.07,0.21 -0.07,0.22 -0.07,0.21 -0.05,0.11 -0.04,0.1 -0.05,0.11 -0.05,0.1 c -0.6,1.22 -1.46,1.87 -1.56,1.87 -0.06,0 -0.1,-0.04 -0.1,-0.1 0,-0.03 0,-0.05 0.19,-0.23 0.98,-0.98 1.55,-2.56 1.55,-4.64 0,-1.69 -0.37,-3.44 -1.61,-4.69 -0.13,-0.12 -0.13,-0.14 -0.13,-0.17 0,-0.06 0.04,-0.1 0.1,-0.1 0.1,0 1,0.67 1.59,1.93 0.51,1.1 0.63,2.2 0.63,3.03 z"
         font-size-adjust="none"
         font-stretch="normal"
         font-style="normal"
         font-variant="normal"
         font-weight="normal"
         letter-spacing="normal"
         stroke-miterlimit="10.433"
         word-spacing="normal"
         style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:white;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
         id="path10294-1" />
         <!-- The ')' in 'f(x)' on the y-axis -->
      </g>
      <line
      x1="-323" y1="497.57214" x2="1300" y2="497.57214" transform="translate(0,0) rotate(0)" id="lineExt2" style="stroke:#6208b6" stroke-width="2"/>
      <!-- This line is used for testing purposes to see if the drawing animations line up exactly, it is defualted to hidden and only seen when made visible, in the end this can be removed-->
  </g>
    
</svg> 

</body>
        </iv-visualisation>
    </div>
</template>
<script>
import vue_config from '../../vue.config.js'
export default {
    name:"second",
    data(){
        return {
            pageName:"Second",
            derivDisp: 1,
            vue_config
        }
    },
    mounted(){
    let vm = this;
        var MODULE = (function () {
    "use strict";
    var that = {},
      t = 0, T = 1, f = 60,
      ivl, iFn, lastFrame;



    var fn=sessionStorage.getItem("funcType") || "exp", oldfn=sessionStorage.getItem("funcType") || "exp", p=1; // Default: start with sine if there is no value for "funcType"
    // c, o, t used for taylor series
    var c1=1, c2=0, c3=0; // current c0 etc.
    var o1=1, o2=0, o3=0; // old c0 etc.
    var t1=1, t2=0, t3=0; // target c0 etc.
    var X0 = [0,0], dX = [0,0], z00=0.45, z0 = 0.45;;
    var el = that.el = {};
  
    var fnOnChange;
    var xScale, yScale, xScale_1, yScale_1;
    let xDiff;
    let animTime = "8s";
    const override = new Event('animationend');
    let minVal;
    let clicked;
    let layerOffset; // Shifts mouse x input by how far the pane on the left covers the screen, otherwise the input would be off

    /* Defines functions mathematically.
      These functions have been scaled - presumably for aesthetic reasons
      */
    var fns = {
      "sin" : function (z) {
        return Math.sin(3 * 2 * Math.PI * z);
      },
      "exp" : function (z) {
        return 3*Math.exp(-5*z);
      },
      "tan" : function (z) {
        return Math.tan(3 * 2 * Math.PI * z);
      },
      "gauss" : function (z) {
        return Math.exp(-Math.pow((z-0.5)/0.1,2)/2);
      },
      "parab" : function (z) {
        return 20*(z-0.5)*(z-0.5)-2.5;
      },
      "parabStep" : function (z) {
        return 20*(z-0.5)*(z-0.5)-2.5 + ((z<0.6)?0:2);
      },
      "poly" : function (x) {
        return ((8*(x-0.5))**6/6 - 3*(8*(x-0.5))**4 - 2*(8*(x-0.5))**3/3 + 27*(8*(x-0.5))**2/2 + 18*(8*(x-0.5)) - 30) / 100*3;
      }
    }
    /* First derivates of the functions in the fns object. This could be useful for
      the second page of our vis
      */
    var fn1s = { // First Derivative
      "sin" : function (z) {
        return (3 * 2 * Math.PI * Math.cos(3 * 2 * Math.PI * z));
      },
      "exp" : function (z) {
        return (-3*5*Math.exp(-5*z));
      },
      "tan" : function (z) {
        return (6*Math.PI/Math.pow(Math.cos(3 * 2 * Math.PI * z), 2));
      },
      "gauss" : function (z) {
        return (Math.exp(-Math.pow((z-0.5)/0.1,2)/2)*(0.5-z)/0.1/0.1);
      },
      "parab" : function (z) {
        return (2*20*(z-0.5));
      },
      "poly" : function (x) {
        return (8*((8*(x-0.5))**5 - 12*(8*(x-0.5))**3 - 2*(8*(x-0.5))**2 + 27*(8*(x-0.5)) + 18) / 100*3);
      }
    }
    fn1s["parabStep"] = fn1s["parab"]
    /* This function is called when the function is changed and performs the 
      animation
      */
    fnOnChange = function (funcChange) {
      funcChange = funcChange || false;
      z0 = funcChange ? z0 : 0;
      el["animButton"].disabled = true; // Prevents button spamming and a glitch that messes with the graphs during the animation
      if(funcChange) {
        el["rect"].dispatchEvent(override);
        el["rect"].classList.remove("full");

        oldfn = fn; // Store the original function as oldfn
        fn = el["function"].value; // Find the new function from the dropdown box
        sessionStorage.setItem("funcType", fn); // Saves the current function on screen to a locally stored variable so that it can be passed over to the other page
        el["func"].children[0].setAttribute("xlink:href", `#${fn}Colourmask`); // Applies the respective colour filter to the appropriate function
      }
      clearInterval(ivl); // Reset the animation
      // Set t=0 at current time, and prepare to increment t inside setInterval
      lastFrame = +new Date;
      t=0;
      let shift = funcChange ? 1 : parseFloat(animTime.substring(0, animTime.length -1))
      /* setInterval repeatedly calls the function iFn with delay 1000/60
        At 60 fps the animation takes 1000ms
        */
      ivl = setInterval(iFn, 1000/f, funcChange, shift);
    };
    /* iFn gives the frame of the animation depending on the time 
      which is given by t, calculated using Date 
      */
    iFn = function (funcChange, shift) {
      var now, x;
      now = +new Date;
      t += (now - lastFrame)/1000;
      if(!funcChange){
        el["checkbox"].checked ? el["lineExt2"].setAttribute("visibility", "visible") : el["lineExt2"].setAttribute("visibility", "hidden"); // Only shows link between graphs when checkbox is ticked during animation
        z0 = t/shift; // If the button was clicked, linearly increase z0 from 0 to 1 during the animation window, this shifts the gradient along the x axis
      } else{
        el["lineExt2"].setAttribute("visibility", "hidden"); // Hides link while display function is changing
      }
      lastFrame = now;
      // if t > T, we stop the animation
      if (t > T*shift) {
        el["lineExt2"].setAttribute("visibility", "hidden"); // Hide link after animation is completed
        clearInterval(ivl);
        el["animButton"].disabled = false; // Once the animation ends the button will be available to use
        // c1, c2, c3 are for interpolating the Taylor series approximations
        o1 = c1 = t1;
        o2 = c2 = t2;
        o3 = c3 = t3;
        p = 1; // When p=1 the displayed function will fully be the new function
        oldfn = fn;
        that.redraw();
        return;
      }
      /* otherwise, calculate an interpolation of the old function and new function
        using the x definition to make it ease in rather than linear.
        */
      x = (1 - Math.cos(Math.PI * t / T)) / 2;
      // c1, c2, c3 are for interpolating the Taylor series approximations
      c1 = o1 + (t1 - o1) * x;
      c2 = o2 + (t2 - o2) * x;
      c3 = o3 + (t3 - o3) * x;
      p = x;
      that.redraw();
    };
  
    that.redraw = function () {
      var x0 = 55.123835, y0 = 497.57214; // Page Coordinates
      var xOffset = 0.0001;
      var fxStr = "";
      let f1xStr = "";
      var f, inRange;
      let f1, inRange1, adj;

      switch(fn) { // Gets the scaling adjustements for each derivative
        case "sin":
          adj = 19;
          break;
        case "exp":
        case "parab":
        case "parabStep":
          adj = 5;
          break;
        case "tan":
          adj = 15;
          break;
        case "gauss":
          adj = 7;
          break;
        case "poly":
          adj = 10;
      }

      /* This draws each of the functions, including when animation is running, by
        calculating the function at 512 points and drawing straight lines between
        each point
      */
      for (var i = 0; i < 512; i += 1) {
        //
        f = p*fns[fn](i/512) + (1-p)*fns[oldfn](i/512) || 0
        f1 = p*fn1s[fn](i/512)/adj + (1-p)*fn1s[oldfn](i/512)/adj || 0

        inRange = Math.abs(f) < 4;
        inRange1 = Math.abs(f1) < 4;

        f = Math.min(Math.max(f, -4), 4)
        f1 = Math.min(Math.max(f1, -4), 4)

        fxStr += ((i && inRange)?" L ":" M ") + (x0 + xScale*i/512) + "," + (y0 + yScale * f)
        f1xStr += ((i && inRange1)?" L ":" M ") + (x0 + xScale_1*i/512) + "," + (y0 + yScale_1 * f1)

      }

      el["fx"].setAttribute("d", fxStr);
      el["fx-1"].setAttribute("d", f1xStr);

      el["blob"].setAttribute("d", "M " + (x0+xScale*z0) + "," + y0 + " L " + (x0+xScale*z0) + "," + (y0+yScale* (p*fns[fn](z0) + (1-p)*fns[oldfn](z0)) ));
      el["blob2"].setAttribute("d", "M " + (x0+xScale*z0 + xOffset) + "," + y0 + " L " + (x0+xScale*z0 + xOffset) + "," + (y0+yScale* (p*fns[fn](z0 + xOffset/xScale) + (1-p)*fns[oldfn](z0 + xOffset/xScale)) ));

      let angle = Math.atan2((y0+yScale* (p*fns[fn](z0 + xOffset/xScale) + (1-p)*fns[oldfn](z0 + xOffset/xScale))) - (y0+yScale* (p*fns[fn](z0) + (1-p)*fns[oldfn](z0))), (x0+xScale*z0 + xOffset) - (x0+xScale*z0)) * 180 / Math.PI;
      let excess = 577 - (y0+yScale* (p*fns[fn](z0) + (1-p)*fns[oldfn](z0))); // This calculates what the x2 attibute of lineExt2 should be to show the link between the two graphs as the derivative is being drawn
      excess += (y0+yScale* (p*fn1s[fn](z0)/adj + (1-p)*fn1s[oldfn](z0)/adj)) - 497.57214;
      
      el["lineExt"].setAttribute("transform", `translate(${((x0+xScale*z0)+(x0+xScale*z0 + xOffset))/2 - xDiff}, ${((y0+yScale* (p*fns[fn](z0) + (1-p)*fns[oldfn](z0)))+(y0+yScale* (p*fns[fn](z0 + xOffset/xScale) + (1-p)*fns[oldfn](z0 + xOffset/xScale))))/2 - y0}) rotate(${angle}, ${xDiff}, ${y0})`);
      el["lineExt2"].setAttribute("transform", `translate(${((x0+xScale*z0)+(x0+xScale*z0 + xOffset))/2 - xDiff}, ${((y0+yScale* (p*fns[fn](z0) + (1-p)*fns[oldfn](z0)))+(y0+yScale* (p*fns[fn](z0 + xOffset/xScale) + (1-p)*fns[oldfn](z0 + xOffset/xScale))))/2 - y0}) rotate(90, ${xDiff}, ${y0})`);
      el["lineExt2"].setAttribute("x2", `${excess}`);

      // Display value of gradient
      var zOffset = xOffset/xScale;
      var gradient = ((fns[fn](z0 + zOffset) - fns[fn](z0))/zOffset)/18.8;
      
      vm.derivDisp = gradient.toFixed(2).toString();
    };
  
    // This function runs when the page loads (see <body> tag in index.html)
    that.init = function () {

      // Create an array of the elements using their ids and getElementById
      ["root", "graph", "function", "xAxis", "yAxis", "xAxis-1", "yAxis-1", "fx", "fx-1", "blob", "blob2", "lineExt", "animButton", "rect", "duration", "lineExt2", "gradientDisplayVal1",
      "gradientDisplayVal2","gradientDisplayValx1", "gradientDisplayValx2", "gradientDisplayValdx1","gradientDisplayValdx2", "limitDisplay", "gradientDisplay", "func", "checkbox", "pane"].map(

        function (id) {
          el[id] = document.getElementById(id);
        });

      el["func"].children[0].setAttribute("xlink:href", `#${fn}Colourmask`); // Applies the correct colour filter to the function which was brought over by the previous page

      // This allows for us to use variables within the CSS, so the animation duration and how far the clip-path goes is no longer hard coded
      let r = document.querySelector(":root");
      r.style.setProperty('--animDuration', animTime);
      el["lineExt2"].setAttribute("visibility", "hidden");
      xDiff = (parseFloat(el["lineExt"].getAttribute('x1')) + parseFloat(el["lineExt"].getAttribute("x2"))) / 2;
      clicked = false;
      minVal = 0.0001;
      el["lineExt"].setAttribute("stroke-dasharray", "0");
      // When "function" changes, animate the change
      el["function"].onchange = fnOnChange;
  
      // Find the size of the bounding box in pixels
      xScale = el["xAxis"].getBBox().width;
      yScale = -el["yAxis"].getBBox().height / 2 / 3;
      const axisWidth = xScale + "px";
      r.style.setProperty('--axis-width', axisWidth);

      xScale_1 = el["xAxis-1"].getBBox().width;
      yScale_1 = -el["yAxis-1"].getBBox().height / 2 / 3;
  
      // Set the cursor to pointer mode when hovering over the graph
      el["graph"].style.cursor = "pointer";
      X0 = [el["blob"].getBBox().x + 207, el["blob"].getBBox().y];
  
      // Create mousePressed variable, set to false by default
      var mousePressed = false;
      // When the mouse is moved over the graph,
      el["graph"].onmousemove = function (e) {
        /* If the mouse is not pressed, set the cursor to pointer mode 
          and prevent any default events */
        if (!mousePressed) {
          el["graph"].style.cursor = clicked ? "default" : "pointer"; // Visually shows user that they cannot interact with the graph while animation is playing
          return e.preventDefault();
        }
        // Otherwise, set the cursor to grab mode
        el["graph"].style.cursor = "grabbing";
        // Find the position of the cursor
        let paneWidth = el["pane"].getAttribute("style");
        paneWidth = parseInt(paneWidth.substring(6, paneWidth.length - 3));
        layerOffset = -paneWidth;
        dX = [e.clientX - X0[0] + layerOffset, e.clientY - X0[1]] // +layerOffset adjusts mouse pos input for when the side pane is shown
        // Scale the x component of the mouse position between 0 and 1
        z0 = Math.min(Math.max(z00 + dX[0]/xScale, 0), 1);
        // Redraw the graph
        that.redraw();
        return e.preventDefault();
      };
  
      // Perform the onmousemove function when the mouse is pressed down
      el["graph"].onmousedown = function (e) {
        mousePressed = clicked ? false: true; // Disables user's ability to interact with the graph while animation is playing
        return el["graph"].onmousemove(e);
      };
      
      // This function animates the two graphs when the button is clicked
      el["animButton"].onclick = function(){
        el["graph"].style.cursor = "default"; // This removes a glitch that causes the cursor to be pointer for a split second
        r.style.setProperty('--animDuration', animTime);
        if (!clicked) { // Prevents button spamming
          fnOnChange(false); // Makes use of the function used to animate the first graph changing functions,, but to change z0 instead
        }
        clicked = true;
        el["rect"].classList.remove("full"); // Resets clip-path animation if already played
        el["rect"].classList.add("r"); // Adds the derivative animation
        that.redraw();
        el["rect"].addEventListener("animationend", function() { // Once the animation has ended this block of code runs
          el["rect"].classList.remove("r"); // Remove derivative animation
          el["rect"].classList.add("full"); // Sustains the derivative graph
          clicked = false; // Allows user to now press the button again this "clicked" flag could be removed as we could disable the button instead
          el["graph"].style.cursor = "pointer"; // Visually shows the user that they can now interact with the graph
          that.redraw();
        });
      }
      // on mouse up, set mousePressed to false
      el["graph"].onmouseup = function (e) {
        mousePressed = false;
        return e.preventDefault();
      };
  
      // Prevent default drag behaviour on "root"
      el["root"].ondragstart = function (e) { return e.preventDefault(); };
  
      // Set fn to the value in "function" and draw the graph for the first time
      el["function"].value = fn;
      that.redraw()
  
      document.body.onclick = null;

    };
  
    return that;



  }());
  MODULE.init();


    }
}
</script>
   <style>
      :root{
         --animDuration: 1s;
         --axis-width: 512px;
      }
      .full {
         width: var(--axis-width);
      }
      .r {
            animation: move var(--animDuration) linear;
        }
        @keyframes move {
            to {
                width: var(--axis-width);
            }
        }
        body, svg{
          height: 100%;
          min-height: 850px;
          overflow: hidden;
        }
      </style>