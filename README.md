# argparse
A C++ Command Line Parser

Supported API：
void add_argument(std::string long_string, std::string default_string = "",
            std::string help_string = "");
ArgumentParser &long_name(const std::string &long_name);
ArgumentParser &short_name(const std::string &short_name);
ArgumentParser &positional_name(const std::string name);
// default
ArgumentParser &default_value(const std::string &default_value);
ArgumentParser &default_value(const char *temp);
ArgumentParser &default_value(const int default_value);
ArgumentParser &default_value(const double default_value);
ArgumentParser &default_value(const bool default_value);
ArgumentParser &default_value(const std::vector<std::string> &default_value);
ArgumentParser &default_value(const std::vector<int> &default_value);
ArgumentParser &default_value(const std::vector<double> &default_value);
ArgumentParser &default_value(const std::vector<bool> &default_value);
// const - if nargs='?' or action='store_const'
ArgumentParser &const_value(const std::string &const_value);
ArgumentParser &const_value(const char *temp);
ArgumentParser &const_value(const int const_value);
ArgumentParser &const_value(const double const_value);
ArgumentParser &const_value(const bool const_value);
ArgumentParser &const_value(const std::vector<std::string> const_value);
ArgumentParser &const_value(const std::vector<int> const_value);
ArgumentParser &const_value(const std::vector<double> const_value);
ArgumentParser &const_value(const std::vector<bool> const_value);
// help
ArgumentParser &help(const std::string &help);
ArgumentParser &help(const char *help);
// nargs ? | + | * |  N
ArgumentParser &nargs(const std::string &nargs_type);
ArgumentParser &nargs(const int nargs_number);
// action store_false / store_true / store_const
ArgumentParser &action(const std::string &store_para);
// dest - rename key
ArgumentParser &dest(const std::string &dest);
// choices
ArgumentParser &choices(const std::vector<std::string> &string_array);
ArgumentParser &choices(const std::vector<int> &int_array);
ArgumentParser &choices(const std::vector<double> &double_array);
ArgumentParser &choices(const std::vector<bool> &bool_array);
// type : std::string int float bool
ArgumentParser &type(const ValueType value_type);
// submit a entry
void done();
// parse arguments
ArgValue parse_args_any_type(int argc, char *argv[]);
std::map<std::string, std::string> parse_args_string(int argc, char *argv[]);

Sample Code:
You can Register API in any legal order， submit a entry with API done()
ArgValue init_args(int argc, char *argv[]) {
  ArgumentParser argument_parser;
  argument_parser.short_name("-m").default_value("abc").done();
  return argument_parser.parse_args_any_type(argc, argv);
}
You can get value:
std::string m_value = arg_result.get_value<std::string>("m");
