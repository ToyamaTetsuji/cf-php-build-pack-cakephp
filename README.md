CloudFoundry PHP Build pack を使ってIBM BlueMixで cakephp2 を動かすように対応したものです


CloudFoundry PHP Build packのDocumentRootが
IBM BlueMixだとhtdocs(/home/vcap/app/htdocs/)
なので
htdocs/app/webrootにするように
defaults/config/httpd/2.4.x/httpd.conf内の

         DocumentRoot "${HOME}/htdocs"
を

         DocumentRoot "${HOME}/htdocs/app/webroot"

と書き換えただけです

ただ、これだけだとどうもうまくいかないので
cakephpのrootにあるindex.phpの38行目の

         define('CAKE_CORE_INCLUDE_PATH', ROOT . DS . 'lib');
を

         define('CAKE_CORE_INCLUDE_PATH', ROOT . DS . '../lib');

と書き換えてあげてください


本当はcf-exを作るべきなんでしょうね



### License

This software includes the work that is distributed in the [Apache License 2.0].


[Apache License 2.0]:http://www.apache.org/licenses/LICENSE-2.0
