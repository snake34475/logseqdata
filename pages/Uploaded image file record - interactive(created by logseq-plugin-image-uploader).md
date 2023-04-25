- #+BEGIN_QUERY
  {:title "Not uploaded images"
    :query [:find (pull ?b [*])
          :where
          [?b :block/page ?p]
          [?p :block/name ?page_name]
          (not [(clojure.string/includes? ?page_name "created by logseq-plugin-image-uploader")])
          [?b :block/content ?content]
          (not [(clojure.string/includes? ?content "{:title \"Not uploaded images\"")])
          [(clojure.string/includes? ?content "](../assets")]
          [(clojure.string/includes? ?content "![")]
          (or [(clojure.string/includes? ?content ".png)")]
              [(clojure.string/includes? ?content ".jpg)")]
              [(clojure.string/includes? ?content ".jpeg)")]
              [(clojure.string/includes? ?content ".gif)")]
              [(clojure.string/includes? ?content ".tiff)")]
              [(clojure.string/includes? ?content ".tif)")]
              [(clojure.string/includes? ?content ".bmp)")]
              [(clojure.string/includes? ?content ".svg)")]
              [(clojure.string/includes? ?content ".webp)")]
              [(clojure.string/includes? ?content ".PNG)")]
              [(clojure.string/includes? ?content ".JPG)")]
              [(clojure.string/includes? ?content ".JPEG)")]
              [(clojure.string/includes? ?content ".GIF)")]
              [(clojure.string/includes? ?content ".TIGG)")]
              [(clojure.string/includes? ?content ".TIF)")]
              [(clojure.string/includes? ?content ".VMP)")]
              [(clojure.string/includes? ?content ".SVG)")]
              [(clojure.string/includes? ?content ".WEBP)")])
        ]}
  #+END_QUERY
	- ![Uploaded by Image Uploder](../assets/image_1680865314623_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1680865314623_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1680951225605_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681449664327_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681449908347_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681449948275_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681450083861_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681450136522_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681450593906_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681450326814_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681450326814_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681872721069_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681872781842_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681872836616_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1681873174112_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1682421427361_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1682421427361_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1682421427361_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1682421499530_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1682421843225_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1682421987181_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1682422086006_0.png)
	- ![Uploaded by Image Uploder](../assets/image_1682422121342_0.png)