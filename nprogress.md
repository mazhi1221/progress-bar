### 项目添加 nprogress 进度条

## 1.安装依赖包
    yarn add nprogress -s

## 2.main.js 中导入依赖包和样式
    import NProgress from 'nprogress'
    import 'nprogress/nprogress.css'

## 3.在 axios 请求拦截器和响应拦截器中配置启动和结束
    // 添加请求拦截器
    request.interceptors.request.use(
        function (config) {
        // 在发送请求之前做些什么
        NProgress.start()
        return config;
    },
    function (error) {
        // 对请求错误做些什么
        return Promise.reject(error);
    }
    );
    // 添加响应拦截器
    request.interceptors.response.use(
        function (response) {
        // 2xx 范围内的状态码都会触发该函数。
        // 对响应数据做点什么
        NProgress.done()
        return response;
    },
    function (error) {
        // 超出 2xx 范围的状态码都会触发该函数。
        // 对响应错误做点什么
        return Promise.reject(error);
    }
    );