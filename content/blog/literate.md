---
{
	"type" : "blog",
	"author" : "Branquinho",
	"title" : "SICMUtils excellent library",
	"description" : "Symbolic and Numerical solutions to Lagrangeans in Clojure.",
	"image": "images/article-covers/newton-lambda.jpg",
	"published": "2021-06-10",
}
---

In this post, you will se some SCIMutils in use. Did you know you can generate euler-lagrangean's solution by simply stating the Lagragian (Kinetic energy minus Potential energy) of a system? I, personally, find that amusing.

So, there we go. Let's render these beauties into TeX.

Also, check out the awesome project for making Physics as easy as building block's concatenation. 

# Table of Contents

1.  [Preamble Structure](#org7ef2e90)
    1.  [project.clj](#orgb8b5c8f)
2.  [Sicmutils](#org8dbc3aa)
    1.  [Name Space (ns)](#orga4b872a)
    2.  [Simple render examples](#orgcc87e9d)
    3.  [Simple tex-render example](#org168702e)
    4.  [Double Pendulum Lagrangian](#orgf1c0152)
3.  [Understanding the library](#orgd00605f)
    1.  [Debugging and behaviour study](#org013d6be)



<a id="org7ef2e90"></a>

# Preamble Structure


<a id="orgb8b5c8f"></a>

## project.clj

    (defproject sicmutils-org "0.1.0-SNAPSHOT"
      :description "FIXME: write description"
      :url "http://example.com/FIXME"
      :license {:name "EPL-2.0 OR GPL-2.0-or-later WITH Classpath-exception-2.0"
    	    :url "https://www.eclipse.org/legal/epl-2.0/"}
      :dependencies [[org.clojure/clojure "1.10.3"]
    		 [sicmutils/sicmutils "0.18.0"]
    		 [aerial.hanami/aerial.hanami "0.12.7"]
    		 [uncomplicate/neanderthal "0.41.0"]
    		 [uncomplicate/fluokitten "0.9.1"]
    		 [uncomplicate/clojurecuda "0.13.0"]
    		 [uncomplicate/clojurecl "0.15.0"]
    		 [generateme/fastmath "2.1.1"]
    		 [incanter/incanter "1.9.3"]
    		 [uncomplicate/commons "0.12.0"]
    		 ;; [scicloj/tablecloth "5.05"]
    		 [org.bytedeco/mkl-platform-redist "2021.1-1.5.5"]
    		 ;; [criterium "0.4.4"]
    		 ;; [findmyway/plotly-clj "0.1.1"]
    		 ;; [hiccup "1.0.5"]
    		 ;; [org.clojure/data.json  "0.2.6"]
    		 ;; [net.mikera/core.matrix "0.57.0"]
    		 ;; [com.rpl/specter "0.13.2"] 
    		 ;; [http-kit  "2.2.0"]
    		 ;; [lein-gorilla "0.4.0"]
    		 ;; [org.clojure/data.csv "0.1.3"]
    		 ;; [clj-commons/pomegranate "1.2.1"]
    		 ]
      :exclusions [[org.jcuda/jcuda-natives :classifier "apple-x86_64"]
    	       [org.jcuda/jcublas-natives :classifier "apple-x86_64"]]
      ;; :plugins [[lein-gorilla "0.4.0"]]
      :main ^:skip-aot sicmutils-org.core
      :target-path "target/%s"
      :profiles {:uberjar {:aot :all
    		       :jvm-opts ^:replace [#_"--add-opens=java.base/jdk.internal.ref=ALL-UNNAMED"]}})


<a id="org8dbc3aa"></a>

# Sicmutils


<a id="orga4b872a"></a>

## Name Space (ns)

    (ns sicmutils-org.sicmutils1
      (:require [sicmutils.env :as env]))
    (env/bootstrap-repl!)


<a id="orgcc87e9d"></a>

## Simple render examples

    (def render (comp ->infix simplify))
    
    (square (sin (+ 'a 3)))
    ;;=> (expt (sin (+ a 3)) 2)
    
    (render (square (sin (+ 'a 3))))
    ;;=> "sin??(a + 3)"


<a id="org168702e"></a>

## Simple tex-render example

    (def render-tex (comp ->TeX simplify))
    (render-tex
     (simplify ((D cube) 'x)))


<a id="orgf1c0152"></a>

## Double Pendulum Lagrangian

    (defn L-central-polar [m U]
      (fn [[_ [r] [rdot thetadot]]]
        (- (* 1/2 m
    	  (+ (square rdot)
    	     (square (* r thetadot))))
           (U r))))

    (let [potential-fn (literal-function 'U)
          L     (L-central-polar 'm potential-fn)
          state (up (literal-function 'r)
    		(literal-function 'theta))]
      ;; (render-tex)
      (((Lagrange-equations L) state) 't))
    ;;=> "down(- m r(t) (D??(t))?? + m D??r(t) + DU(r(t)), m (r(t))?? D????(t) + 2 m r(t) Dr(t) D??(t))"

\begin{bmatrix}\displaystyle{- m\,r\left(t\right)\,{\left(D\theta\left(t\right)\right)}^{2} + m\,{D}^{2}r\left(t\right) + DU\left(r\left(t\right)\right)}& \\
\displaystyle{m\,
{\left(r\left(t\right)\right)}^{2}\,{D}^{2}\theta\left(t\right) + 2\,m\,r\left(t\right)\,D\theta\left(t\right)\,Dr\left(t\right)}\end{bmatrix}

    (def L-free-fall
      (fn [[t q qdot]]
        (+ 'E0
         (- (- (* 1/2 'm (square qdot))
    	   (* 'm 'g (square q)))
    	(* 1/2 'k (square qdot))))))
    
    (def y (literal-function 'y))
    
    (render-tex (((Lagrange-equations L-free-fall) y) 't))

\(2\,g \,m \,y \left(t \right) - k \,{D}^{2}y \left(t \right) + m \,{D}^{2}y \left(t \right) = 0\)

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">#'sicmutils-org.sicmutils1/L-free-fall</td>
</tr>


<tr>
<td class="org-left">#'sicmutils-org.sicmutils1/y</td>
</tr>


<tr>
<td class="org-left">class java.lang.ClassCastException</td>
</tr>
</tbody>
</table>

\(2\,g\,m\,y\left(t\right) - k\,{D}^{2}y\left(t\right) + m\,{D}^{2}y\left(t\right) = 0\)

\(2 \,g \,m \,y \left(t \right) -2 \,k \,{D}^{2}y \left(t \right) + m\,{D}^{2}y \left(t \right) = 0\)

\(2 \,g \,m \,y \left(t \right) + m \,{D}^{2}y \left(t \right) = 0\)

\(\, {D}^{2}y \left( t \right) =  -g\)

    (->JavaScript (((Lagrange-equations L-free-fall) y) 't))


<a id="orgd00605f"></a>

# Understanding the library

We use [sicmutils's doc](https://cljdoc.org/d/sicmutils/sicmutils/0.18.0/doc/reference-manual) as a guide.

    (kind 3.14)

    ((kind-predicate 3.14) 1)

    ((kind-predicate 3.14) 1.0)

    ((fn [x] (- (one-like x) x)) [[1 2] [2 1]])
    ((fn [x] (- (zero-like x) x)) [1 2])
    ((fn [x] (- (zero-like x) x)) 3)

    (def M
      (matrix-by-rows [1  2  3  4  5]
    		  [6  7  8  9 10]
    		  [11 12 13 14 15]))

    (map cos (nth M 1))

    ;; (rows M) => [n m]
    ;; (count M) ;; => n
    ;; (count (nth M 1)) ;; => m
    
    (defn dim [matrix]
      [(count matrix) (count (nth matrix 1))])

    (dim M)

    (defn matrix:elementwise [proc m]
      (let [[rows columns] (dim m)]
        (m:generate rows columns
    		(fn [i j] (proc (get-in m [i j]))))))

    (matrix:elementwise cos M)

    (def N [['a11 'a12]['a21 'a22]])

    (matrix:elementwise cos N)

    (matrix:elementwise D (matrix:elementwise cos N))


<a id="org013d6be"></a>

## Debugging and behaviour study

    (defn foo [x m]
      (let [[i j] (dim m)]
        [x m]))

    (defn element-proc [proc m i j]
      (proc (ref m i j)))

Ok, let's stop here. More on next posts.
