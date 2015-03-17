# Загрузка динамических ENGINE (GOST) #

```
    ENGINE_load_builtin_engines;
    ENGINE_load_dynamic;

         E := ENGINE_by_id('dynamic');
         if E = nil then
          raise Exception.Create('Dynamic engine not loaded!');
         SSL_CheckError;
         if ENGINE_cmd_is_executable(e, 200) = 1 then
           ENGINE_ctrl_cmd_string(e, 'SO_PATH', PAnsiChar(GostLib), 0);
         SSL_CheckError;
         ENGINE_ctrl_cmd_string(e, 'LIST_ADD', '2', 0);
         ENGINE_ctrl_cmd_string(e, 'LOAD', nil, 0);
         ENGINE_set_default_string(e, 'ALL');
         ENGINE_ctrl_cmd_string(e, 'CRYPT_PARAMS', 'id-Gost28147-89-CryptoPro-A-ParamSet', 0);
         ENGINE_free(e);

```