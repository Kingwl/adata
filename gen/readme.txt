adlʹ��˵��

�ȿ����򵥵����ӣ����������һ��ȫò

sub_type
{
  string str;
}

test_type
{
  int8             i8 = 1;
  fix_uint32       fu32 = 56;
  string           str;
  list<int32>      int_list;
  map<int16,int32> i16_i32_map;  //����һ���ֵ�����
  sub_type         sub;
}

adata�����ƣ�
1. C++ head only������Ҫ����⣬ֻҪһ��ͷ�ļ��߱����£���ƽ̨(windows/linux/macos)
2. Depend nothing, û�е������������ (����js����long.js��)���ɾ���ˬһ����
3. �����ԣ�Ŀǰ֧��C++,lua(luajit),js,C#���պ�ƻ�����java��go��֧�֣���ӭ־Ը�߼������Լ�ϲ����������չ��
4. ƽ���������ɵ����ݶ��������µ����ݶ�������ȷ�Ķ�ȡ

��������
����Ӧ�����࣬�������������л�ʱ�ᰴ��ֵ�Ĵ�С���е���ռ�õ����ݿռ䣬����С��ֵ�����պ����޸�Ϊ���ֵ���ͣ���֮���ɡ�
int8
uint8
int16
uint16
int32
uint32
int64
uint64

���������࣬�����͵����������л�ʱ��ռ�ù̶������ݿռ䣬���Ҳ����޸�ֵ����
fix_int8
fix_uint8
fix_int16
fix_uint16
fix_int32
fix_uint32
fix_int64
fix_uint64
�����������Ϳ������ó�ʼֵ

��������
float32
float64
�ռ�ռ��ͬ���Ƕ�����Ҳ�����޸�ֵ����

�ַ���
string
�ַ������������42�ڸ��ַ���2^32�������ܴ���ֽ��ַ�������utf8��
�ַ��������Լ����峤�ȼ�⣬�����������л�ʧ�ܣ��ù��ܿ��Է�ֹ������Э����ָ��������ַ������ȣ������·���������

�б�
list
�б�����Դ洢�����Ķ�����ͣ������Զ�������
�б���Ҳ��ָ�����ȼ��

�ֵ�
map
�ֵ�����Դ洢key/value����ɢ�Ķ�����Ͷԣ�value�����Զ�������

�Զ�������
�Զ������͵��������������ƿ�ʼ��"{}"�ж����ֶ���Ϣ
�����������
test_type
{
  fix_int32 i = 1;  //this is a comment �������ע��
  int64 i64 = 8;
}

test_type������������
������Ͷ����������ֶ�
fix_int32 i = 1;  ������32λ�з������ͣ���ʼֵΪ1��ע���ֶζ���������ע��
int64 i64 = 8;    ����Ӧ���ȵ�64λ�з������ͣ��Ƽ���������ͣ����ֵС��128�����л�ʱ�ᱻѹ����1�ֽڣ����Բ��õ��Ŀռ�ռ�õ�����


���涨��һ���ַ���������
test_type
{
  string s(30);
}
string s(30);      ������һ���ַ�������������Ϊ30

���涨��һ���б������
test_type
{
  list<int32>      int_list(50);
  list<string(25)> str_list;
}
list<int32>      int_list;   ������һ������Ӧ����32λ�з��������ĵ��б��б��ȵ�����Ϊ50
list<string(25)> str_list;   ������һ����������Ϊ25���ַ������б�

���涨��һ���ֵ������
test_type
{
  map<int32,fix_uint64>      int2int_map(50);
}
map<int32,fix_uint64>      int2int_map(50);  ������һ������Ӧ����32λ�з���������key������64λ�޷����������ֵ䣬��������Ϊ50
���涨��һ�������Զ������͵�����
sub_type
{
  int32 i = 1;
}
test_type
{
  sub_type sub;
  int64    i64;
}
�ȶ�����һ��sub_type���Զ�������
�ڶ�����һ��test_type
sub_type sub;  ��һ���ֶ�Ϊ�Զ�������sub_type;

�汾��������ʱ�����Э����Ҫ����һ���ֶΣ���ôû���⣬�ɵ�Э�����л������ݿ��������Ķ�ȡ���µ�Э��Ķ�����
������Э����Ҫɾ��һ���ֶΣ��벻Ҫֱ���ڶ��崦ֱ��ɾ������Ӧ����ô��

test_type
{
  int32    i32[delete];
  int64    i64;
}
int32    i32[delete];����ֶν��ᱻ���ԣ����ڱ���ȡ�������ɴ�����Ҳ�������ռλ���µ����л�������Ҳ����ռ�ÿռ�

�Զ�������Ŀǰ�ֶ�����Ϊ63���������İ汾�������չ

adl�ļ��Ŀ�ͷ���Զ��������C++��C#�лᱻת��Ϊnamespace����lua��js�л���Ϊһ��key��Ϊ���Ҽ�
���ĸ�ʽ��
name1.name2.name3 ...��������

idl������
adata_gen.exe -I���adl�ļ� -GҪ����������
-G������ʹ��
Ŀǰ֧�ֵ�������cpp,lua,js,csharp
lua�ֶ�����԰汾lua51,lua52,lua53,luajit
����
�ȶ����һ��test.adl

namespace = test.abc;

sub_type
{
  int32 i = 1;  //this is a comment
  int64 i64 = 8;
}

test
{
  fix_int16 i = 1;
  float32 f = 3.0;
  string s(30);
  list<int32> lis;
  map<int32,int64> ms;
  list<string(25)> ss;
  sub_type sub;   
}

test_delete
{
  fix_int16 i = 1;
  float32 f = 3.0 [delete];
  string s(30);
  list<int32> lis [delete];
  map<int32,int64> ms;
  list<string(25)> ss;
  sub_type sub;
}

����������ݴ浽test.adl�ļ�

adata_gen.exe -Itest.adl -Gcpp
�����ͻ����һ��
test.adl.h
������������Ĺ������棬�Ϳ���ֱ��ʹ����
C++��ʹ������
#include "test.adl.h"
#include <fstream>

std::ostream& dump_test(const ::test::abc::test& value, std::ostream& os)
{
  os << "i: " << value.i << std::endl;
  os << "f: " << value.f << std::endl;
  os << "s: " << value.s << std::endl;
  os << "is: [";
  for (auto& p : value.lis)
  {
    os << p << ",";
  }
  os << "]" << std::endl;
  os << "ms: {";
  for (auto& p : value.ms)
  {
    os << p.first << ": " << p.second << " , ";
  }
  os << "}" << std::endl;
  os << "ss: [";
  for (auto& s : value.ss)
  {
    os << s << ",";
  }
  os << "]" << std::endl;
  os << "sub: (i: " << value.sub.i << ",i64: " << value.sub.i64 << ")" << std::endl;
  return os;
}

void test_adata_save_data()
{
  ::test::abc::test value;

  value.i = 12;
  value.f = 3.45f;
  value.s = "abcdefg";
  value.lis.push_back(67);
  value.lis.push_back(89);
  value.ms[1] = 11;
  value.ms[2] = 22;
  value.ms[3] = 33;
  value.ss.push_back("abc");
  value.ss.push_back("def");
  value.ss.push_back("hij");
  value.sub.i = 12345;
  value.sub.i64 = 10007199254740992LL;

  dump_test(value,std::cout);
  std::string wb_str;
  adata::zero_copy_buffer stream;
  adata::pre_write(value, stream);
  adata::adata_write_link_string(stream, wb_str);
  if (adata::adata_stream_write(stream, value))
  {
    std::ofstream os("test.bin");
    os.write(wb_str.data(), wb_str.length());
    os.close();
  }
}

int main(int argc, char * argv[])
{
   test_adata_save_data();
}

��������ǽ�һ��::test::abc::test���͵Ķ������л���һ���������ļ��У���Ҳ���Խ��䷢�͵�������
����������ļ��Ժ�����������������������л��Ľ������ȷ��
���ǿ�����lua���������ļ������������л���һ��lua��������