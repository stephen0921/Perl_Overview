# Perl_Overview

##前提
* 假设大家看过"Perl入门"这本书

##Perl coding tips

###打开pipe或者访问文件的时候，最好使用die
```perl
  open FILE, "a_file" or die "Can not open file a_file: $!";
  close FILE;
```
###比die更好用的是croak
```perl
  a("a_file");
  b("b_file");
  sub a {
      my $filename = shift;
      open FILE, "$filename" or croak "Can not open file $filename: $!";
      return 0;
  }
```
##Perl 在我们验证中的应用
