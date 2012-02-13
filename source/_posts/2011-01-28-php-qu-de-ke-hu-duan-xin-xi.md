--- 
categories: 
  - PHP
comments: true
layout: post
published: true
status: publish
tags: 
  - code
  - free
  - ie
  - java
  - Linux
  - MAC
  - opera
  - OS
  - php
  - server
  - unix
  - User
  - web
  - win
  - windows
  - 浏览器
title: PHP取得客户端信息
type: post
---
作用：取得客户端信息<br>参数：<br>返回：指定的资料<br>使用：<br>    $code = new clientGetObj;<br>    1、浏览器：$str = $code->getBrowse();<br>    2、IP地址：$str = $code->getIP();<br>    4、操作系统：$str = $code->getOS();<br>*/<br><div> </div>$code = new clientGetObj;<br>echo $code->getBrowse()."<br/>";<br>echo $code->getIP()."<br/>";<br>echo $code->getOS()."<br/>";<br><div> </div>class clientGetObj<br>{<br>    function getBrowse()<br>    {<br>        global $_SERVER;<br>        $Agent = $_SERVER['HTTP_USER_AGENT'];<br>        $browser = '';<br>        $browserver = '';<br>        $Browser = array('Lynx', 'MOSAIC', 'AOL', 'Opera', 'JAVA', 'MacWeb', 'WebExplorer', 'OmniWeb');<br>        for($i = 0; $i <= 7; $i ++){<br>            if(strpos($Agent, $Browsers[$i])){<br>                $browser = $Browsers[$i];<br>                $browserver = '';<br>            }<br>        }<br>        if(mb_ereg('Mozilla', $Agent) && !mb_ereg('MSIE', $Agent)){<br>            $temp = explode('(', $Agent);<br>            $Part = $temp[0];<br>            $temp = explode('/', $Part);<br>            $browserver = $temp[1];<br>            $temp = explode(' ', $browserver);<br>            $browserver = $temp[0];<br>            $browserver = preg_replace('/([d.]+)/', '\1', $browserver);<br>            $browserver = $browserver;<br>            $browser = 'Netscape Navigator';<br>        }<br>        if(mb_ereg('Mozilla', $Agent) && mb_ereg('Opera', $Agent)) {<br>            $temp = explode('(', $Agent);<br>            $Part = $temp[1];<br>            $temp = explode(')', $Part);<br>            $browserver = $temp[1];<br>            $temp = explode(' ', $browserver);<br>            $browserver = $temp[2];<br>            $browserver = preg_replace('/([d.]+)/', '\1', $browserver);<br>            $browserver = $browserver;<br>            $browser = 'Opera';<br>        }<br>        if(mb_ereg('Mozilla', $Agent) && mb_ereg('MSIE', $Agent)){<br>            $temp = explode('(', $Agent);<br>            $Part = $temp[1];<br>            $temp = explode(';', $Part);<br>            $Part = $temp[1];<br>            $temp = explode(' ', $Part);<br>            $browserver = $temp[2];<br>            $browserver = preg_replace('/([d.]+)/','\1',$browserver);<br>            $browserver = $browserver;<br>            $browser = 'Internet Explorer';<br>        }<br>        if($browser != ''){<br>            $browseinfo = $browser.' '.$browserver;<br>        } else {<br>            $browseinfo = false;<br>        }<br>        return $browseinfo;<br>    }<br><div> </div>    function getIP ()<br>    {<br>        global $_SERVER;<br>        if (getenv('HTTP_CLIENT_IP')) {<br>            $ip = getenv('HTTP_CLIENT_IP');<br>        } else if (getenv('HTTP_X_FORWARDED_FOR')) {<br>            $ip = getenv('HTTP_X_FORWARDED_FOR');<br>        } else if (getenv('REMOTE_ADDR')) {<br>            $ip = getenv('REMOTE_ADDR');<br>        } else {<br>            $ip = $_SERVER['REMOTE_ADDR'];<br>        }<br>        return $ip;<br>    }<br><div> </div>    function getOS ()<br>    {<br>        global $_SERVER;<br>        $agent = $_SERVER['HTTP_USER_AGENT'];<br>        $os = false;<br>        if (mb_eregi('win', $agent) && strpos($agent, '95')){<br>            $os = 'Windows 95';<br>        }<br>        else if (mb_eregi('win 9x', $agent) && strpos($agent, '4.90')){<br>            $os = 'Windows ME';<br>        }<br>        else if (mb_eregi('win', $agent) && mb_ereg('98', $agent)){<br>            $os = 'Windows 98';<br>        }<br>        else if (mb_eregi('win', $agent) && mb_eregi('nt 5.1', $agent)){<br>            $os = 'Windows XP';<br>        }<br>        else if (mb_eregi('win', $agent) && mb_eregi('nt 5', $agent)){<br>            $os = 'Windows 2000';<br>        }<br>        else if (mb_eregi('win', $agent) && mb_eregi('nt', $agent)){<br>            $os = 'Windows NT';<br>        }<br>        else if (mb_eregi('win', $agent) && mb_ereg('32', $agent)){<br>            $os = 'Windows 32';<br>        }<br>        else if (mb_eregi('linux', $agent)){<br>            $os = 'Linux';<br>        }<br>        else if (mb_eregi('unix', $agent)){<br>            $os = 'Unix';<br>        }<br>        else if (mb_eregi('sun', $agent) && mb_eregi('os', $agent)){<br>            $os = 'SunOS';<br>        }<br>        else if (mb_eregi('ibm', $agent) && mb_eregi('os', $agent)){<br>            $os = 'IBM OS/2';<br>        }<br>        else if (mb_eregi('Mac', $agent) && mb_eregi('PC', $agent)){<br>            $os = 'Macintosh';<br>        }<br>        else if (mb_eregi('PowerPC', $agent)){<br>            $os = 'PowerPC';<br>        }<br>        else if (mb_eregi('AIX', $agent)){<br>            $os = 'AIX';<br>        }<br>        else if (mb_eregi('HPUX', $agent)){<br>            $os = 'HPUX';<br>        }<br>        else if (mb_eregi('NetBSD', $agent)){<br>            $os = 'NetBSD';<br>        }<br>        else if (mb_eregi('BSD', $agent)){<br>            $os = 'BSD';<br>        }<br>        else if (mb_ereg('OSF1', $agent)){<br>            $os = 'OSF1';<br>        }<br>        else if (mb_ereg('IRIX', $agent)){<br>            $os = 'IRIX';<br>        }<br>        else if (mb_eregi('FreeBSD', $agent)){<br>            $os = 'FreeBSD';<br>        }<br>        else if (mb_eregi('teleport', $agent)){<br>            $os = 'teleport';<br>        }<br>        else if (mb_eregi('flashget', $agent)){<br>            $os = 'flashget';<br>        }<br>        else if (mb_eregi('webzip', $agent)){<br>            $os = 'webzip';<br>        }<br>        else if (mb_eregi('offline', $agent)){<br>            $os = 'offline';<br>        }<br>        else {<br>             $os = 'Unknown';<br>        }<br>        return $os;<br>    }<br><div> </div>}<br>?><br>
</div>
<div><a title="Wiz，个人知识管理，PKM。" href="http://wiz.cn">通过Wiz发布</a></div>