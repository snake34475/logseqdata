- webpack-bundle-analyzer可视化
	- umi配置
		- ```js
		  //config/config.js
		  import { BundleAnalyzerPlugin } from "webpack-bundle-analyzer"
		  export default {
		     // 添加 BundleAnalyzerPlugin
		      if (process.env.ANALYZE) {
		        config.plugin('webpack-bundle-analyzer').use(BundleAnalyzerPlugin, [{ analyzerPort: 8889 }]);
		      }
		  }
		  //.env
		  ANALYZE=true umi dev //只有测试开启
		  ```
- [优化1](https://juejin.cn/post/6911519627772329991)
- [优化2](https://juejin.cn/post/7081453829375393823)
-