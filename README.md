```javascript
// 遷移先画面への受け渡し用変数を初期化
$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.display_list = [];
$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list = [];
$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list = [];
// 被告人身柄記録一覧
const hikokunin_migara_list = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source;
// 初期表示時のデータ
const initialdata_list = $variable.elementset_parameter.S153.action_result.http_response.response_data.S153001_LD001.hikokunin_migara_kiroku_list;

// 被告人氏名リスト
const text_list = $variable.elementset_parameter.S153.main.table_setting.column_settings.hikokunin_shimei.optionsText;
const value_list = $variable.elementset_parameter.S153.main.table_setting.column_settings.hikokunin_shimei.optionsValue;
let jiken_mei_info = {
        "zaimei_code": "",
        "zaimei_text": "",
        "moto_zaimei_text": "",
        "henshu_flag": ""
      }

for (let i = 0; i < hikokunin_migara_list.length; i++) {
  // 被告人氏名取得
  let select_index = value_list.findIndex((value) => value == hikokunin_migara_list[i].hikokunin_shimei);//.value);
  let select_shimei = text_list[select_index];
  // 被告人等番号を取得
  //let hikokuninto_bango = hikokunin_migara_list[i].hikokunin_shimei.value.slice(hikokunin_migara_list[i].hikokunin_shimei.value.indexOf(':') + 1);
  //let hikokuninto_bango = hikokunin_migara_list[i].hikokunin_shimei.slice(hikokunin_migara_list[i].hikokunin_shimei.indexOf(':') + 1);
  let hikokuninto_bango = $input.response_data.S152001_LD001.migara_info.migara_info.migara_kiroku[parseInt(hikokunin_migara_list[i].hikokunin_shimei) - 1].hikokuninto_bango;

  // 表示用リストに格納（一覧に表示していたデータすべてを格納）
  $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.display_list.push({
    jiken_code: hikokunin_migara_list[i].jiken_code,
    saibansho_code: hikokunin_migara_list[i].saibansho_code,
    jiken_bango: hikokunin_migara_list[i].jiken_bango,
    shinko_kanri_tani: hikokunin_migara_list[i].shinko_kanri_tani,
    tetsuduki_kanri_id: hikokunin_migara_list[i].tetsuduki_kanri_id,
    hikokuninto_bango: hikokuninto_bango,
    number: i + 1,
    migara_bango: hikokunin_migara_list[i].migara_bango,
    hikokunin_shimei: select_shimei,
    //hikokunin_shimei_value: hikokunin_migara_list[i].hikokunin_shimei.value,
    hikokunin_shimei_value: hikokunin_migara_list[i].hikokunin_shimei,
    koryu_bi: hikokunin_migara_list[i].koryu_bi,
    koryu_bi_moto: hikokunin_migara_list[i].koryu_bi_moto,
    koryu_zaimei: hikokunin_migara_list[i].koryu_zaimei,
    kiso_bi: hikokunin_migara_list[i].kiso_bi,
    kiso_bi_moto: hikokunin_migara_list[i].kiso_bi_moto,
    kiso_zaimei: hikokunin_migara_list[i].kiso_zaimei,
    daiikai_kohanzumi_flag: hikokunin_migara_list[i].daiikai_kohanzumi_flag,
    jiken_saishu_koshin_nichiji: hikokunin_migara_list[i].jiken_saishu_koshin_nichiji,
    sansho_kengen_flag: hikokunin_migara_list[i].sansho_kengen_flag,
    kiroku_kanri_bango: hikokunin_migara_list[i].kiroku_kanri_bango,
    kiso_zaimei_joho : [{
      zaimei_code: "",
      zaimei_text: "",
      moto_zaimei_text: "",
      henshu_flag: ""
    }],
    koryu_zaimei_joho : [{
      zaimei_code: "",
      zaimei_text: "",
      moto_zaimei_text: "",
      henshu_flag: ""
    }]
  });


  for(let j = 0; j < $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho.length; j++){
    jiken_mei_info.zaimei_code = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].zaimei_code;
    jiken_mei_info.zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].zaimei_text;
    jiken_mei_info.moto_zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].moto_zaimei_text;
    jiken_mei_info.henshu_flag = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].henshu_flag;
    $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.display_list[i].kiso_zaimei_joho.push(jiken_mei_info)
  }
  $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.display_list[i].kiso_zaimei_joho.splice(0,1);

  for(let j = 0; j < $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho.length; j++){
    jiken_mei_info.zaimei_code = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].zaimei_code;
    jiken_mei_info.zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].zaimei_text;
    jiken_mei_info.moto_zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].moto_zaimei_text;
    jiken_mei_info.henshu_flag = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].henshu_flag;
    $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.display_list[i].koryu_zaimei_joho.push(jiken_mei_info)
  }
  $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.display_list[i].koryu_zaimei_joho.splice(0,1);


  if (i < $variable.elementset_parameter.S153.sub.initialdata_length && initialdata_list[i].koryu_bi != null && initialdata_list[i].koryu_bi != '') {
    // 一覧の項目のいずれかが変更されたかチェック
    if (select_shimei != initialdata_list[i].hikokunin_shimei ||
      hikokunin_migara_list[i].koryu_zaimei != initialdata_list[i].kiso_zaimei ||
      hikokunin_migara_list[i].kiso_zaimei != initialdata_list[i].kiso_zaimei ||
      hikokunin_migara_list[i].koryu_bi_moto.getFullYear() != initialdata_list[i].koryu_bi_moto.getFullYear() ||
      hikokunin_migara_list[i].koryu_bi_moto.getMonth() != initialdata_list[i].koryu_bi_moto.getMonth() ||
      hikokunin_migara_list[i].koryu_bi_moto.getDate() != initialdata_list[i].koryu_bi_moto.getDate() ||
      hikokunin_migara_list[i].kiso_bi_moto.getFullYear() != initialdata_list[i].kiso_bi_moto.getFullYear() ||
      hikokunin_migara_list[i].kiso_bi_moto.getMonth() != initialdata_list[i].kiso_bi_moto.getMonth() ||
      hikokunin_migara_list[i].kiso_bi_moto.getDate() != initialdata_list[i].kiso_bi_moto.getDate()) {
      // update_listに追加
      $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list.push({


        jiken_code: hikokunin_migara_list[i].jiken_code,
        saibansho_code: hikokunin_migara_list[i].saibansho_code,
        jiken_bango: hikokunin_migara_list[i].jiken_bango,
        shinko_kanri_tani: hikokunin_migara_list[i].shinko_kanri_tani,
        tetsuduki_kanri_id: hikokunin_migara_list[i].tetsuduki_kanri_id,
        hikokuninto_bango: hikokuninto_bango,
        number: i + 1,
        migara_bango: hikokunin_migara_list[i].migara_bango,
        hikokunin_shimei: select_shimei,
        koryu_bi: hikokunin_migara_list[i].koryu_bi,
        koryu_bi_moto: hikokunin_migara_list[i].koryu_bi_moto,
        koryu_zaimei: hikokunin_migara_list[i].koryu_zaimei,
        kiso_bi: hikokunin_migara_list[i].kiso_bi,
        kiso_bi_moto: hikokunin_migara_list[i].kiso_bi_moto,
        kiso_zaimei: hikokunin_migara_list[i].kiso_zaimei,
        daiikai_kohanzumi_flag: hikokunin_migara_list[i].daiikai_kohanzumi_flag,
        jiken_saishu_koshin_nichiji: hikokunin_migara_list[i].jiken_saishu_koshin_nichiji,
        sansho_kengen_flag: hikokunin_migara_list[i].sansho_kengen_flag,
        kiroku_kanri_bango: hikokunin_migara_list[i].kiroku_kanri_bango,
        kiso_zaimei_joho : [{
          zaimei_code: "",
          zaimei_text: "",
          moto_zaimei_text: "",
          henshu_flag: ""
        }],
        koryu_zaimei_joho : [{
          zaimei_code: "",
          zaimei_text: "",
          moto_zaimei_text: "",
          henshu_flag: ""
        }]
      });


      for(let j = 0; j < $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho.length; j++){
        jiken_mei_info.zaimei_code = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].zaimei_code;
        jiken_mei_info.zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].zaimei_text;
        jiken_mei_info.moto_zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].moto_zaimei_text;
        jiken_mei_info.henshu_flag = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].henshu_flag;
        $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list[$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list.length - 1].kiso_zaimei_joho.push(jiken_mei_info)
      }
      // ★修正: update_list[i] → 最後の要素
      $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list[$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list.length - 1].kiso_zaimei_joho.splice(0,1);

      for(let j = 0; j < $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho.length; j++){
        jiken_mei_info.zaimei_code = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].zaimei_code;
        jiken_mei_info.zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].zaimei_text;
        jiken_mei_info.moto_zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].moto_zaimei_text;
        jiken_mei_info.henshu_flag = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].henshu_flag;
        // ★修正: update_list[i] → 最後の要素
        $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list[$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list.length - 1].koryu_zaimei_joho.push(jiken_mei_info)
      }
      // ★修正: update_list[i] → 最後の要素
      $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list[$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.update_list.length - 1].koryu_zaimei_joho.splice(0,1);
    };
  } else {
    // add_listに追加
    $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list.push({
      jiken_code: hikokunin_migara_list[i].jiken_code,
      saibansho_code: hikokunin_migara_list[i].saibansho_code,
      jiken_bango: hikokunin_migara_list[i].jiken_bango,
      shinko_kanri_tani: hikokunin_migara_list[i].shinko_kanri_tani,
      tetsuduki_kanri_id: hikokunin_migara_list[i].tetsuduki_kanri_id,
      hikokuninto_bango: hikokuninto_bango,
      number: i + 1,
      migara_bango: hikokunin_migara_list[i].migara_bango,
      hikokunin_shimei: select_shimei,
      koryu_bi: hikokunin_migara_list[i].koryu_bi,
      koryu_bi_moto: hikokunin_migara_list[i].koryu_bi_moto,
      koryu_zaimei: hikokunin_migara_list[i].koryu_zaimei,
      kiso_bi: hikokunin_migara_list[i].kiso_bi,
      kiso_bi_moto: hikokunin_migara_list[i].kiso_bi_moto,
      kiso_zaimei: hikokunin_migara_list[i].kiso_zaimei,
      daiikai_kohanzumi_flag: hikokunin_migara_list[i].daiikai_kohanzumi_flag,
      sansho_kengen_flag: hikokunin_migara_list[i].sansho_kengen_flag,
      kiroku_kanri_bango: hikokunin_migara_list[i].kiroku_kanri_bango,
      kiso_zaimei_joho : [{
        zaimei_code: "",
        zaimei_text: "",
        moto_zaimei_text: "",
        henshu_flag: ""
      }],
      koryu_zaimei_joho : [{
        zaimei_code: "",
        zaimei_text: "",
        moto_zaimei_text: "",
        henshu_flag: ""
      }]
    });

    for(let j = 0; j < $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho.length; j++){
      jiken_mei_info.zaimei_code = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].zaimei_code;
      jiken_mei_info.zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].zaimei_text;
      jiken_mei_info.moto_zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].moto_zaimei_text;
      jiken_mei_info.henshu_flag = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].kiso_zaimei_joho[j].henshu_flag;
      // ★修正: add_list[i] → 最後の要素
      $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list[$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list.length - 1].kiso_zaimei_joho.push(jiken_mei_info)
    }
    // ★修正: add_list[i] → 最後の要素
    $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list[$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list.length - 1].kiso_zaimei_joho.splice(0,1);

    for(let j = 0; j < $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho.length; j++){
      jiken_mei_info.zaimei_code = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].zaimei_code;
      jiken_mei_info.zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].zaimei_text;
      jiken_mei_info.moto_zaimei_text = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].moto_zaimei_text;
      jiken_mei_info.henshu_flag = $variable.elementset_parameter.S153.main.screen_data.table_data.hikokunin_migara_kiroku.data_source[i].koryu_zaimei_joho[j].henshu_flag;
      // ★修正: add_list[i] → 最後の要素
      $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list[$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list.length - 1].koryu_zaimei_joho.push(jiken_mei_info)
    }
    // ★修正: add_list[i] → 最後の要素
    $variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list[$variable.elementset_parameter.S153.sub.migara_joho_hikokunin.add_list.length - 1].koryu_zaimei_joho.splice(0,1);

  };
};
```
