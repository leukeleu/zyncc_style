# Zyncc style

This exposes the basic CSS of Zyncc. It can be used like this in your main js file:

    require('zyncc_style');
    require('./index.pcss'); // the main styling file of your project

Some PCSS variables included in this package (`variables.js`) can also be exported to the rest of your CSS files (in the webpack2 flavour):

    var cssSettings = require('zyncc_style/variables.js');
    
    module.exports = function(debug) {
    var config = {
        /* ... */
        module: {
            loaders: [
                /* ... */
                {
                    test: /\.pcss$/,
                    use: [
                        'style-loader',
                        { loader: 'css-loader', options: { importLoaders: 1 } },
                        { loader: 'postcss-loader', options: {
                            plugins: function () {
                                return [
                                    require('postcss-import'),
                                    require('postcss-cssnext')({
                                        features: cssSettings
                                    })
                                ]
                            }
                        }}
                    ]
                }
                /* ... */
            ]
        }
    };
    
TODO: Get images from zyncc
TODO: get preprocessed css from zyncc?