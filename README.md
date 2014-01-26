# Monome

Stolen from https://github.com/meta-ex/ignite. This is purely for my own use, watch @overtone + @meta-ex + @samaaron for the proper extraction of this lib. It will be miles better than this.

Monome-serial is taken from my own locally installed snapshot: https://github.com/josephwilk/monome-serial/tree/protocols

This adds support for multiple Monome protocols.


## Kit

### Sample triggering

Stolen from the masterful Meta-ex https://github.com/meta-ex/ignite

```clojure
(use 'monome.core)
(use 'overtone.live)
(require '[monome.fonome :as fon])
(require '[monome.polynome :as poly])

(require '[monome.kit.sampler :as samp])

(def samples-g (group "samples"))

(def m128 (find-monome "/dev/tty.usbserial-m0000965"))

(defonce trigger-samples [(sample (freesound-path 86773)) (sample (freesound-path 77305))])

(defonce trigger-sampler128  (samp/mk-sampler ::trigger-sampler128 trigger-samples samples-g 0 16))

;;Dock trigger-sampler to 0x0 position on grid
(defonce __dock_trigger__ (poly/dock-fonome! m128
                                             (:fonome trigger-sampler128)
                                             ::trigger-sampler128
                                             0 0))
```
