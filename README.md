# Perl_Overview
##ǰ��
*�����ҿ���"Perl����"�Ȿ��
##Perl coding tips
###��pipe���߷����ļ���ʱ�����ʹ��die
```perl
  open FILE, "a_file" or die "Can not open file a_file: $!";
  close FILE;
```
###��die�����õ���croak
```perl
  a("a_file");
  b("b_file");
  sub a {
      my $filename = shift;
      open FILE, "$filename" or croak "Can not open file $filename: $!";
      return 0;
  }
```
##Perl ��������֤�е�Ӧ��
