### ajax 实际项目中请求的注意：
   - 请求超时设置
   ``` javascript
    var ajaxTimeOutLuckyDraw = $.ajax({
                                type: 'GET',
                                cache: false,
                                async: true, // 使用异步加载
                                url: lotteryRandom,
                                timeout: 10000,
                                data: {
                                    roomId: roomId,
                                    rowId: rowId,
                                    cutType: 'x' + str
                                },
                                headers: {
                                    "token": token
                                },
                                complete: function(XMLHttpRequest, status) { //当请求完成时调用函数
                                    // console.log(XMLHttpRequest, status);
                                    if (status == 'timeout') { 
                                    //status == 'timeout'意为超时,status的可能取值：success,notmodified,nocontent,error,timeout,abort,parsererror 
                                        hideLoadingDialog(null);
                                        ajaxTimeOutLuckyDraw.abort(); //取消请求
                                        bridge.call("app.showMsg", '请求超时，请稍后重试！');
                                    }
                                },
                                success: function(res) {
                                    hideLoadingDialog(null);
                                    chouzhongPrize = (JSON.parse(res)).data;
                                    chouzhongAllPrizeManys = (JSON.parse(res));
                                    console.log(chouzhongAllPrizeManys);
                                    if (chouzhongAllPrizeManys.status == 0) {
                                        // 抽中时执行事件：
                                        toSuccessLuckyDraw();
                                        roll(); //转圈过程不响应click事件，会将click置为false
                                        click = true; //一次抽奖完成后，设置click为true，可继续抽奖
                                        return false;
                                    } else if (chouzhongAllPrizeManys.status == 400) {
                                        // 钻石不足 $("#showLuckyDraw").fadeIn();
                                        $('.showIsNoMoneyToast').fadeIn();
                                        $('.showIsNoMoneyToast .waiButton input').eq(0).off('click').on('click', function() {
                                            $(".showIsNoMoneyToast").fadeOut();
                                        })
                                        $('.showIsNoMoneyToast .waiButton input').eq(1).off('click').on('click', function() {
                                            $(".showIsNoMoneyToast").fadeOut();
                                            showRecharge(null);
                                        })
                                    }
                                },
                                error: function(result, type, err) {
                                    hideLoadingDialog(null);
                                    bridge.call("app.showMsg", '服务器异常！');
                                }
                            });
   ```
   - err设置
   - 微信、qq的二次分享处理 https://www.cnblogs.com/heavenYJJ/p/9445521.html
