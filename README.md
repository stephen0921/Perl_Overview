##前提
* 假设是看过"Perl入门"这本书
![Learning Perl](LearningPerl.PNG)

##Perl coding tips

###打开pipe或者访问文件的时候，最好使用die

```perl
open FILE, "a_file" or die "Can not open file a_file: $!";
close FILE;
```

###比die更好用的是croak

```perl
use Carp;
a("a_file"); #假设a_file存在
a("b_file"); #假设b_file不存在
sub a {
      my $filename = shift;
      open FILE, "$filename" or croak "Can not open file $filename: $!";
      return 0;
}
```

###用dumper来print复杂的数据结构，便于debug

```perl
use Data::Dumper;

$var = {"name" => "hello", "action" => "speak" };
print Dumper($var);
```
###用grep和map可以节省很多代码

```perl
my @foos = grep {!/^#/} @bars;    # weed out comments

my %hash = map {  lc($_) => 1  } @array

my @squares = map { $_ * $_ } grep { $_ > 5 } @numbers;
```

###使用qq代替双引号，使用q代替单引号，list赋值使用qw

```perl
$a = qq{"}; #{}只是边界作用
$b = qq!"!; #和上面是一样的

$c = q{'};
@vars = qw{a b c};
```

###使用list的内置函数，不要重新发明轮子

```perl
use List::Util qw(max);

my @vars = qw(1 2 3);
my $result = max(@vars);
```

###打印多行的信息

```perl
$a = "hello";
print <<ENDOFPRINT;
Dear Lee,
    blablabla...
    $a
ENDOFPRINT

$b = <<ENDOFA;
Dear friend,
   I am here.
ENDOFA
```

###只想做语法检查

```shell
perl -cwT test.pl
```

###查看Perl默认的include路径

```shell
perl -e "print join(\"\n\", @INC)"
```

###使用自己的local路径下的库

```perl
use lib '/home/xx/eda_scripts/pm';
```
###查看perl的pod格式的说明

```shell
perldoc rvp.pm
perldoc perldoc
```

###Perl5.8之后的版本，可以在数据中间加下划线

```perl
$a = 111_222;
print "a = ", $a , "\n";
```

###安装module
```shell
cpan install Template
cpan install XML::Rabbit #反应了目录层次
```

###好用的module

* [Template](http://template-toolkit.org/docs/)
* [XML::LibXML](http://search.cpan.org/~shlomif/XML-LibXML-2.0125/LibXML.pod)
* [XML::Rabbit](http://search.cpan.org/~robins/XML-Rabbit-0.4.1/lib/XML/Rabbit.pm)
* [rvp](http://www.burbleland.com/v2html/rvp.html)
* [Smart::Comments](http://search.cpan.org/~neilb/Smart-Comments-1.06/lib/Smart/Comments.pm)
* 

##Perl 在我们验证中的应用

##Perl 参考书目，以及推荐阅读顺序
![Books](books.PNG)


