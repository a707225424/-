# match
简单描述正则使用案例 

<?php
$str = '<dl>
		<dt>第一个标题</dt>
		<dd>111112</dd>
		<dd>111112</dd>
		<dd>111112</dd>
		<dd>22222</dd>
		<dd>111122222212</dd>
		<dd>111112</dd>
		<dd>111112</dd>
		<dt>第二个标题</dt>
		<dd>2222222</dd>
		<dd>2222222</dd>
		<dd>2222222</dd>
		<dd>2222222</dd>
		<dd>2222222</dd>
		<dd>2222222</dd>
		<dd>2222222</dd>
	</dl>';
//$str = 'http://baidu.com';
//$pattern = '/http:\/\/.*com/';//需要转义/

//查找第二个dt之后的全部内容 1匹配第一个dt 2匹配第一个dt与第二个dt之间的内容 3匹配第二个dt 4匹配需要的内容
$pattern = '/.*<dt[\s\S]*<\/dt>[\s\S]*<dt[\s\S]*<\/dt>([\s\S]*)<\/dl>/';//需要转义/

preg_match($pattern,$str,$match);

//var_dump($match);

$str2 = '<dd>22222221</dd><dd>222222223</dd><dd>22222223</dd><dd>22222242</dd><dd>22222522</dd><dd>22226222</dd><dd>22227222</dd>';
//获取dd标签中的内容，任意匹配
$pattern2 = '/.*?<dd>([\S]*?)<\/dd>.*?/';//需要转义/

preg_match_all($pattern2,$str2,$match2);

var_dump($match2);




$str = '<div class="c1s">
  <li><a href="#">111111111</a></li>
  <li><a href="#">222222222</a></li>
  <li><a href="#">333333333</a></li>
  <li><a href="#">444444444</a></li>
</div>';
 
// 如果内容很多，可以首先匹配出div中的内容
preg_match('/<div class=\"c1s\">(.*?)<\/div>/is',$str,$re);
// 匹配li中的内容
preg_match_all('/<li><a href=\"(.*?)\">(.*?)<\/a><\/li>/is',$re[1],$lt);
 
var_dump($lt[2]);// 这就是你想要的结果
?>
