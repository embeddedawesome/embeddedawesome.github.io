# Template engine functions

## dir(\<filename\>)
Returns the directory portion of a filename
## "notdir"
    return std::filesystem::path{ args.at(0)->get<std::string>() }.filename();
  });
##   "glob"
    nlohmann::json aggregate = nlohmann::json::array();
    std::vector<std::string> string_args;
    for (const auto &i: args)
      string_args.push_back(i->get<std::string>());
    for (auto &p: glob::rglob(string_args))
      aggregate.push_back(p.generic_string());
    return aggregate;
  });
## "absolute_dir"
    const auto path = std::filesystem::path{ args.at(0)->get<std::string>() };
    return std::filesystem::absolute(path).generic_string();
  });
## "absolute_path"
    const auto path = std::filesystem::path{ args.at(0)->get<std::string>() };
    return std::filesystem::absolute(path).generic_string();
  });
## "relative_path"
    auto path          = std::filesystem::path{ args.at(0)->get<std::string>() };
    const auto current = std::filesystem::current_path();
    auto new_path      = std::filesystem::relative(path, current);
    return new_path.generic_string();
  });
## "relative_path", 2
    const auto path1 = args.at(0)->get<std::string>();
    const auto path2 = std::filesystem::absolute(args.at(1)->get<std::string>());
    return std::filesystem::relative(path1, path2).generic_string();
  });
## "extension"
    return std::filesystem::path{ args.at(0)->get<std::string>() }.extension().string().substr(1);
  });
## "filesize"
    return fs::file_size(args[0]->get<std::string>());
  });
## "file_exists"
    return fs::exists(args[0]->get<std::string>());
  });
## "hex2dec"
    return std::stoul(args[0]->get<std::string>(), nullptr, 16);
  });
## "read_file"
    auto file = std::ifstream(args[0]->get<std::string>());
    return std::string{ std::istreambuf_iterator<char>{ file }, {} };
  });
## "load_yaml"
    const auto file_path = args[0]->get<std::string>();
    if (std::filesystem::exists(file_path)) {
      auto yaml_data = YAML::LoadFile(file_path);
      return yaml_data.as<nlohmann::json>();
    } else {
      return nlohmann::json();
    }
  });
## "load_json"
    std::ifstream file_stream(args[0]->get<std::string>());
    return nlohmann::json::parse(file_stream);
  });
## quote(\<string\>)
Quotes the input string 

## replace(\<input string\>, \<regex string\>, \<match expression\>)
Applies a regex_replace call on the provided string.

Example:
> `{{ replace("my input string", "st(.*)", "$1")}}`

Output
> `"my input ring"`

## regex_escape(\<string\>)
Sanitize the provided string for use as a regular expression