'''Java
    
    List<String> strList = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().contains("/")) {
            if (url.getPath().contains("add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].contains("s")) {
                    if (parameters[1].contains("anewstringtoadd")) {
                        strList = new ArrayList<String>();
                        return String.format("%s", strList);
                    } else {
                        strList.add(parameters[1]);
                        return String.format("%s", strList);
                    }
                } else {
                    return "404 Not Found!";
                }
            } else if (url.getPath().contains("search")) {
                String[] parameters = url.getQuery().split("=");
                List<String> found = new ArrayList<String>();

                if (parameters[0].contains("s")) {

                    for (String str : strList) {
                        if (str.contains(parameters[1])) {
                            found.add(str);
                        }
                    }
                }
                return String.format("%s", found);

            } else {
                return String.format("%s", strList);
            }
        }
        return "404 Not Found!";
    }
}

'''
