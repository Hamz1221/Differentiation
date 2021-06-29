<template>
    <div>
        <iv-visualisation :title="pageName" :vue_config="vue_config" :page_number="1">
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

                  <iv-fixed-hotspot position="topleft" title="Equation" style="z-index:2; width:0px; height:0px;" transparent>
                        <div style="border-top:200px; width:300px; height:0px;" v-if="deltaDist !== '0.00'">
                          <img src="../assets/equationBlankOrig.svg" style="position: relative; left:600px; top: 100px; -webkit-filter: invert(1); filter: invert(1);"/>
                          <p style="position: relative; left:870px; top:45px; -webkit-filter: invert(1); filter: invert(1);">= {{derivDisp}}</p>
                          <p style="position: relative; left:813px; top:-8px; -webkit-filter: invert(1); filter: invert(1); font-size: 12pt;">{{xValDisp}}</p>
                          <p style="position: relative; left:675px; top:-42px; -webkit-filter: invert(1); filter: invert(1); font-size: 12pt;">{{xValDisp}}</p>
                          <p style="position: relative; left:730px; top:-78px; -webkit-filter: invert(1); filter: invert(1); font-size: 12pt;">{{deltaDist}}</p>
                          <p style="position: relative; left:750px; top:-86px; -webkit-filter: invert(1); filter: invert(1); font-size: 12pt;">{{deltaDist}}</p>
                        </div>

                        <div style="border-top:200px;" v-if="deltaDist == '0.00'">
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
                      <br>

                      Delta x:
                      <input type="range" min="0.0001" max="100" value="25" class="slider" id="deltaX" name="deltax" step="0.0001" style="width:188px;margin-top:19px;margin-bottom:14px;">
                    

                    

                    </div>

                    
  
                  
                 </iv-toggle-hotspot>
            </template>
    <div>
<body style="overflow: hidden; margin: 0; position:relative" id="body">

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
   height="673" 
   width="100%"
   >
   <!-- h=500, w-570 -->
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
         style="fill-rule:evenodd;stroke:white;stroke-width:1pt;stroke-opacity:1;fill:#5DFF33;fill-opacity:1"
         d="M -2.5,-1.0 C -2.5,1.7600000 -4.7400000,4.0 -7.5,4.0 C -10.260000,4.0 -12.5,1.7600000 -12.5,-1.0 C -12.5,-3.7600000 -10.260000,-6.0 -7.5,-6.0 C -4.7400000,-6.0 -2.5,-3.7600000 -2.5,-1.0 z "
         id="path9112" />
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
         id="path7898" />
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
    </marker>
    <radialGradient
       gradientUnits="userSpaceOnUse"
       gradientTransform="matrix(-0.65523826,0,0,-0.6247619,1172.0929,131.92585)"
       r="280"
       fy="105.07805"
       fx="447.40897"
       cy="105.07805"
       cx="447.40897"
       id="radialGradient4581"
       xlink:href="#linearGradient4579" />
    <linearGradient
       id="linearGradient4579">
      <stop
         id="stop4575"
         offset="0"
         style="stop-color:#7aaed7;stop-opacity:1" />
      <stop
         id="stop4577"
         offset="1"
         style="stop-color:#466589;stop-opacity:1" />
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
         style="color:white;display:inline;overflow:visible;visibility:visible;opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:nonzero;stroke:#f0f5fa;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;paint-order:stroke fill markers;enable-background:accumulate"
         id="rect19349"
         width="528"
         height="400"
         x="47.123837"
         y="297.57214" />
    </clipPath>
  </defs>
  <g
     transform="translate(-23.123835,-221.57211)"
     id="layer1">
     <!-- url(#radialGradient4581-1) -->
    <rect
       style="color:white;display:inline;overflow:hidden;visibility:visible;opacity:1;vector-effect:none;fill:url(#radialGradient4581-1);fill-opacity:1;fill-rule:nonzero;stroke:none;stroke-width:0.99999994;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;paint-order:stroke fill markers;enable-background:accumulate"
       id="rect4573-0"
       width="100%"
       height="1000000"
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
       style="fill: #7aaed7; stroke: black;"
       id="right-side-pane"
       x="650"
       y="250"
       width="400"
       height="500"
       pathLength="2800"
       transform="translate(0,-2)"/>   -->
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
         id="g9544">
        <path
           id="yAxis"
           d="m 55.123835,689.57214 v -384"
           style="opacity:1;vector-effect:none;fill:#f0f5fa;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-end:url(#marker7900);paint-order:stroke fill markers" />
        <path
           id="xAxis"
           d="M 55.123835,497.57214 H 567.12383"
           style="opacity:1;vector-effect:none;fill:#f0f5fa;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-end:url(#TriangleOutM);paint-order:stroke fill markers" />
      </g>
      <path
         style="opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:evenodd;stroke:#afdb85;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1;marker:none;paint-order:stroke fill markers"
         d="M 55.123835,497.57214 H 567.12383"
         id="fx" />
      <line
         x1="-1000" y1="497.57214" x2="1300" y2="497.57214" transform="translate(0,0) rotate(0)" id="lineExt" style="stroke:#ff0505" stroke-width="2"/>
         <!-- This is the line that is the extension of the line between the two points -->
      <path
         style="opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:evenodd;stroke:#ff0000;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-start:url(#marker9114);marker-end:url(#marker9114);paint-order:stroke fill markers"
         d="m 55.123835,497.57214 v 0"
         id="blob" />
       <path
         style="opacity:1;vector-effect:none;fill:none;fill-opacity:1;fill-rule:evenodd;stroke:#ff0000;stroke-width:2;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:4;stroke-dasharray:2, 2;stroke-dashoffset:0;stroke-opacity:1;marker:none;marker-start:url(#marker9114);marker-end:url(#marker9114);paint-order:stroke fill markers"
         d="m 55.123835,497.57214 v 0"
         id="blob2" />
      <!-- <circle cx="55.123835" cy="497.57214" r="10"/> The Origin of the axises-->
      
    </g>
    <g
       style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:#f0f5fa;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0.5;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"
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
       id="content"><path
         style="fill:white;stroke-width:0"
         id="path10149"
         d="m 306.11,698.17 v 0.03 l 0.01,0.03 0.01,0.03 0.01,0.03 0.01,0.04 0.01,0.04 0.01,0.05 0.02,0.04 0.01,0.05 0.02,0.05 0.02,0.04 0.02,0.05 0.02,0.05 0.03,0.05 0.02,0.05 0.03,0.05 0.03,0.05 0.03,0.05 0.04,0.04 0.03,0.05 0.04,0.04 0.04,0.04 0.04,0.04 0.04,0.04 0.05,0.03 0.05,0.03 0.03,0.01 0.02,0.01 0.03,0.01 0.02,0.01 0.03,0.01 0.03,0.01 0.03,0.01 h 0.03 l 0.03,0.01 h 0.03 0.03 0.04 c 0.04,0 0.28,0 0.49,-0.13 -0.28,-0.05 -0.48,-0.3 -0.48,-0.53 0,-0.16 0.12,-0.35 0.38,-0.35 0.22,0 0.54,0.18 0.54,0.58 0,0.51 -0.59,0.65 -0.92,0.65 -0.58,0 -0.93,-0.53 -1.05,-0.75 -0.25,0.65 -0.79,0.75 -1.08,0.75 -1.04,0 -1.6,-1.28 -1.6,-1.53 0,-0.1 0.1,-0.1 0.11,-0.1 0.09,0 0.12,0.02 0.13,0.11 0.34,1.05 1,1.3 1.34,1.3 0.19,0 0.54,-0.09 0.54,-0.66 0,-0.31 -0.17,-0.98 -0.54,-2.37 -0.16,-0.61 -0.51,-1.03 -0.95,-1.03 -0.06,0 -0.29,0 -0.49,0.13 0.24,0.05 0.46,0.26 0.46,0.54 0,0.26 -0.22,0.34 -0.37,0.34 -0.29,0 -0.54,-0.26 -0.54,-0.57 0,-0.46 0.5,-0.66 0.93,-0.66 0.66,0 1.02,0.7 1.05,0.76 0.12,-0.37 0.48,-0.76 1.08,-0.76 1.02,0 1.59,1.28 1.59,1.53 0,0.1 -0.09,0.1 -0.12,0.1 -0.09,0 -0.11,-0.04 -0.13,-0.11 -0.33,-1.06 -1,-1.3 -1.32,-1.3 -0.39,0 -0.55,0.32 -0.55,0.65 0,0.22 0.06,0.44 0.17,0.88 z" /></g>    <g
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
       style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;letter-spacing:normal;word-spacing:normal;text-anchor:start;fill:#f0f5fa;fill-opacity:1;fill-rule:evenodd;stroke:white;stroke-width:0.5;stroke-linecap:butt;stroke-linejoin:miter;stroke-miterlimit:10.43299961;stroke-dasharray:none;stroke-dashoffset:0;stroke-opacity:1"><path
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
         id="path10288" /><path
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
         id="path10290" /><path
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
         id="path10292" /><path
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
         id="path10294" /></g>
      <!-- <text
       id="text18342"
       y="257.57214"
       x="55.123837"
       style="font-style:normal;font-variant:normal;font-weight:normal;font-stretch:normal;font-size:16px;line-height:125%;font-family:Helvetica;-inkscape-font-specification:Helvetica;text-align:start;letter-spacing:0px;word-spacing:0px;text-anchor:start;fill:#f0f5fa;fill-opacity:1;stroke:none;stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;stroke-opacity:1;"
       xml:space="preserve">
       <tspan
         style="font-size:18.66666603px;text-align:start;text-anchor:start;fill:black;user-select:none;-moz-user-select: none;"
         y="307.57214"
         x="685.123837"
         id="tspan18340">Function</tspan>
      <tspan
         style="font-size:18.66666603px;text-align:start;text-anchor:start;fill:black;user-select:none;-moz-user-select: none;"  
         y="342.57214"
         x="685.123837"
         id="tspan18341">Delta x</tspan>
      </text> -->
   
    <foreignObject
       y="290.90814"
       x="785.80826"
       height="32"
       width="192"
       style="overflow:visible;"
       id="foFunction">
       
    </foreignObject>
  </g>
  <!-- <text id="initText" text-anchor="middle" width="500px" x="50%" y="250" style="fill: white; font-family: Helvetica, Nimbus Sans L, Arial, sans-serif; font-weight: bold; font-size: 24pt;">Click to begin…</text> -->

</svg>

<!--<div class="slidecontainer">
   <input type="range" min="0.0001" max="100" value="25" class="slider" id="deltaX" name="deltax">
   <label for="deltax">Delta x</label>
</div>-->

</body>
</div>
</iv-visualisation>
    </div>
</template>
<script>
import vue_config from '../../vue.config.js'
export default {
    name:"first",
    data(){
        return {
            pageName:"First",
            derivDisp: 0.5,
            xValDisp: 0.4,
            deltaDist: 0.1,
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
    var fn=sessionStorage.getItem("funcType") || "exp", oldfn=sessionStorage.getItem("funcType") || "exp", p=1; // Default: start with sine if there is no value for "funType"
    // c, o, t used for taylor series
    var c1=1, c2=0, c3=0; // current c0 etc.
    var o1=1, o2=0, o3=0; // old c0 etc.
    var t1=1, t2=0, t3=0; // target c0 etc.
    var X0 = [0,0], dX = [0,0], z00=0.45, z0 = 0.45;;
    var el = that.el = {};
    var fnOnChange;
    let layerOffset; // Shifts mouse x input by how far the pane on the left covers the screen, otherwise the input would be off
    var xScale, yScale;
  
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
  
    /* This function is called when the function is changed and performs the 
      animation
      */
    fnOnChange = function () {
      oldfn = fn; // Store the original function as oldfn
      fn = el["function"].value; // Find the new function from the dropdown box
      sessionStorage.setItem("funcType", fn); // Saves the current function on screen to a locally stored variable so that it can be passed over to the other page
      clearInterval(ivl); // Reset the animation
      // Set t=0 at current time, and prepare to increment t inside setInterval
      lastFrame = +new Date;
      t=0;
      /* setInterval repeatedly calls the function iFn with delay 1000/60
        At 60 fps the animation takes 1000ms
        */
      ivl = setInterval(iFn, 1000/f);
    };

    /* iFn gives the frame of the animation depending on the time 
      which is given by t, calculated using Date 
      */
    iFn = function () {
      var now, x;
      now = +new Date;
      t += (now - lastFrame)/1000;
      lastFrame = now;
      // if t > T, we stop the animation
      if (t > T) {
        clearInterval(ivl);
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
      var xOffset = el["deltaX"].valueAsNumber;
      var fxStr = "";
      var f, inRange;

      /* This draws each of the functions, including when animation is running, by
        calculating the function at 512 points and drawing straight lines between
        each point
      */
      for (var i = 0; i < 512; i += 1) {
        //
        f = p*fns[fn](i/512) + (1-p)*fns[oldfn](i/512) || 0
        inRange = Math.abs(f) < 4;
        f = Math.min(Math.max(f, -4), 4)

        fxStr += ((i && inRange)?" L ":" M ") + (x0 + xScale*i/512) + "," + (y0 + yScale * f)
      }

      el["fx"].setAttribute("d", fxStr);
      el["blob"].setAttribute("d", "M " + (x0+xScale*z0) + "," + y0 + " L " + (x0+xScale*z0) + "," + (y0+yScale* (p*fns[fn](z0) + (1-p)*fns[oldfn](z0)) ));
      let blob2Xpos = x0+xScale*z0 + xOffset;
      if (blob2Xpos >= 567.123735){
          blob2Xpos = 567.123735;
          el["deltaX"].value = `${567.123735 - (x0+xScale*z0)}`
          xOffset = el["deltaX"].valueAsNumber; 
      }
      el["blob2"].setAttribute("d", "M " + (blob2Xpos) + "," + y0 + " L " + (blob2Xpos) + "," + (y0+yScale* (p*fns[fn](z0 + xOffset/xScale) + (1-p)*fns[oldfn](z0 + xOffset/xScale)) ));

      // Change line style when not at exact derivative 
      if(xOffset === 0.0001){
        el["lineExt"].setAttribute("stroke-dasharray", "0") 
      } else{
        el["lineExt"].setAttribute("stroke-dasharray", "8 3") 
      }

      let angle = Math.atan2((y0+yScale* (p*fns[fn](z0 + xOffset/xScale) + (1-p)*fns[oldfn](z0 + xOffset/xScale))) - (y0+yScale* (p*fns[fn](z0) + (1-p)*fns[oldfn](z0))), (blob2Xpos) - (x0+xScale*z0)) * 180 / Math.PI;
      const xDiff = (parseFloat(el["lineExt"].getAttribute('x1')) + parseFloat(el["lineExt"].getAttribute("x2"))) / 2;

      el["lineExt"].setAttribute("transform", `translate(${((x0+xScale*z0)+(blob2Xpos))/2 - xDiff}, ${((y0+yScale* (p*fns[fn](z0) + (1-p)*fns[oldfn](z0)))+(y0+yScale* (p*fns[fn](z0 + xOffset/xScale) + (1-p)*fns[oldfn](z0 + xOffset/xScale))))/2 - y0}) rotate(${angle}, ${xDiff}, ${y0})`);      

      // Display value of gradient
      var zOffset = xOffset/xScale;
      var gradient = ((fns[fn](z0 + zOffset) - fns[fn](z0))/zOffset)/18.8;
      
      vm.derivDisp = gradient.toFixed(2).toString();
      vm.xValDisp = (z0 * 6 * Math.PI).toFixed(2).toString();
      vm.deltaDist = (zOffset * 6 * Math.PI).toFixed(2).toString();
    };
  
    // This function runs when the page loads (see <body> tag in index.html)
    that.init = function () {
      // Create an array of the elements using their ids and getElementById
      ["root", "graph", "function", "xAxis", "yAxis", "fx", "blob", "blob2", "lineExt", "deltaX", "pane"].map(
        function (id) {
          el[id] = document.getElementById(id);
        });
  
      sessionStorage.setItem("funcType", fn); // Creates a local variable "funcType" so that we can keep the selected function consistent when moving to other pages

      // When "function" changes, animate the change
      el["function"].onchange = fnOnChange;
      // When "deltaX" changes, redraw the graph
      el["deltaX"].oninput = this.redraw;
  
      // Find the size of the bounding box in pixels
      xScale = el["xAxis"].getBBox().width;
      yScale = -el["yAxis"].getBBox().height / 2 / 3;
  
      // Set the cursor to pointer mode when hovering over the graph
      el["graph"].style.cursor = "pointer";
      // Setting X0 twice? Might be a problem here?
      X0 = [el["blob"].getBBox().x + 207, el["blob"].getBBox().y];
  
      // Create mousePressed variable, set to false by default
      var mousePressed = false
      // When the mouse is moved over the graph,
      el["graph"].onmousemove = function (e) {
        /* If the mouse is not pressed, set the cursor to pointer mode 
          and prevent any default events */
        if (!mousePressed) {
          el["graph"].style.cursor = "pointer";
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
        z0 = Math.min(Math.max(z00 + dX[0]/xScale, 0), 1 - el["deltaX"].valueAsNumber/xScale);
        // Redraw the graph
        that.redraw();
        return e.preventDefault();
      };
  
      // Perform the onmousemove function when the mouse is pressed down
      el["graph"].onmousedown = function (e) {
        mousePressed = true;
        return el["graph"].onmousemove(e);
      };
  
      // on mouse up, set mousePressed to false
      el["graph"].onmouseup = function (e) {
        mousePressed = false;
        return e.preventDefault();
      };

      el["root"].onmouseup = function (e) {
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
<style scoped>
 .iv-pane .iv-pane-navigator{
   background: black;
   box-shadow: none;
 }

</style>