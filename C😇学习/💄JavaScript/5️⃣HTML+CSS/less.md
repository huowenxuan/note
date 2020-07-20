# less

## react16引入less

1. npm eject

2. yarn add less-loader -D

3. 修改webpack.config.js

   ```
   ...
   const sassRegex = /\.(scss|sass)$/;
   const sassModuleRegex = /\.module\.(scss|sass)$/;
   // 添加以下两行
   const lessRegex = /\.less$/;
   const lessModuleRegex = /\.module\.less$/;
   ... 
   
   
   // 在getStyleLoaders函数中添加lessOptions和相应loader
   {
                test: cssModuleRegex,
                use: getStyleLoaders({
                   importLoaders: 1, 
                    sourceMap: isEnvProduction && shouldUseSourceMap, 
                    modules: {
                      getLocalIdent: getCSSModuleLocalIdent,
                   }, 
                  }),
                }, 
                {
                 test: lessRegex, 
                  exclude: lessModuleRegex, 
                  use: getStyleLoaders( 
                   {
                      importLoaders: 1, 
                      sourceMap: isEnvProduction && shouldUseSourceMap, 
                    }, 
                    'less-loader' 
                  ), 
                  sideEffects: true, 
                }, 
               {
                 test: lessModuleRegex, 
                 use: getStyleLoaders(
                    {
                      importLoaders: 1, 
                      sourceMap: isEnvProduction && shouldUseSourceMap,
                      module: true,
                      getLocalIdent: getCSSModuleLocalIdent
                     },
                   'less-loader'
                  ),
               },
   }
   ```

4. 报错`Invalid options object. Less Loader has been initialized using an options ob`

   降级css-loader，安装@5.0.0

   ```
   yarn remove css-loader
   yarn add css-loader@5.0.0 -D
   ```

   

