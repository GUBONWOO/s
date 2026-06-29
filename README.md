const input = $input.response_data.S151001.jiken_joho
const varibale = $variable.main.screen_data.jiken_joho
const t1 = $variable.main.screen_data.table_data.hikokunin_table
const t3 = $variable.main.screen_data.table_data.hikokunin_table3

// t1, t3 테이블 비교
let tableSame = true

if (!t1 && !t3) {
  // 둘 다 없으면 같음
  tableSame = true
} else if (!t1 || !t3) {
  // 한쪽만 없으면 다름
  tableSame = false
} else if (t1.length != t3.length) {
  tableSame = false
} else {
  for (let i = 0; i < t1.length; i++) {
    if (t1[i].checkBox != t3[i].checkBox) { tableSame = false }
    if (t1[i].uketsuke_bango != t3[i].uketsuke_bango) { tableSame = false }
    if (t1[i].uketsuke_bango_edaban != t3[i].uketsuke_bango_edaban) { tableSame = false }
    if (t1[i].hikokuninto_bango != t3[i].hikokuninto_bango) { tableSame = false }
    if (t1[i].shimei != t3[i].shimei) { tableSame = false }
    if (t1[i].settei != t3[i].settei) { tableSame = false }
    if (t1[i].jiken_mei != t3[i].jiken_mei) { tableSame = false }

    let kisoBiSame = true
    if (t1[i].kiso_bi && t3[i].kiso_bi) {
      kisoBiSame = t1[i].kiso_bi.getTime() == t3[i].kiso_bi.getTime()
    } else {
      kisoBiSame = t1[i].kiso_bi == t3[i].kiso_bi
    }
    if (!kisoBiSame) { tableSame = false }

    if (t1[i].kiso_bi_2 != t3[i].kiso_bi_2) { tableSame = false }
    if (t1[i].benron_bango != t3[i].benron_bango) { tableSame = false }
    if (t1[i].henshu != t3[i].henshu) { tableSame = false }
    if (t1[i].kisoji_no_migara_kubun != t3[i].kisoji_no_migara_kubun) { tableSame = false }
    if (t1[i].kisoji_no_migara_kubun_label != t3[i].kisoji_no_migara_kubun_label) { tableSame = false }
    if (t1[i].jiken_bango_hyojiyo1 != t3[i].jiken_bango_hyojiyo1) { tableSame = false }
    if (t1[i].koryu_saibansho_code != t3[i].koryu_saibansho_code) { tableSame = false }
    if (t1[i].jiken_bango_hyojiyo2 != t3[i].jiken_bango_hyojiyo2) { tableSame = false }
    if (t1[i].tsuikiso_flag != t3[i].tsuikiso_flag) { tableSame = false }
    if (t1[i].sekken_kinshi_flag != t3[i].sekken_kinshi_flag) { tableSame = false }
    if (t1[i].sokketsu_saiban_flag != t3[i].sokketsu_saiban_flag) { tableSame = false }
    if (t1[i].higisha_sekkento_kinshi_kettei_flag != t3[i].higisha_sekkento_kinshi_kettei_flag) { tableSame = false }
    if (t1[i].kobetsu_moshiokuri_jiko_text != t3[i].kobetsu_moshiokuri_jiko_text) { tableSame = false }
    if (t1[i].gaibu_user_id != t3[i].gaibu_user_id) { tableSame = false }
    if (t1[i].tojisha_bango != t3[i].tojisha_bango) { tableSame = false }
    if (t1[i].shimei_kana != t3[i].shimei_kana) { tableSame = false }
    if (t1[i].kokuseki != t3[i].kokuseki) { tableSame = false }
    if (t1[i].tsuyaku_gengo != t3[i].tsuyaku_gengo) { tableSame = false }
    if (t1[i].jisho_flag != t3[i].jisho_flag) { tableSame = false }
    if (t1[i].fusho_flag != t3[i].fusho_flag) { tableSame = false }
    if (t1[i].fusho_joho != t3[i].fusho_joho) { tableSame = false }
    if (t1[i].shokugyo != t3[i].shokugyo) { tableSame = false }
    if (t1[i].yubin_bango != t3[i].yubin_bango) { tableSame = false }
    if (t1[i].jusho != t3[i].jusho) { tableSame = false }
    if (t1[i].jusho2 != t3[i].jusho2) { tableSame = false }
    if (t1[i].denwa_bango != t3[i].denwa_bango) { tableSame = false }
    if (t1[i].fax_bango != t3[i].fax_bango) { tableSame = false }
    if (t1[i].sotatsu_todokedeto_sotatsu_uketorinin != t3[i].sotatsu_todokedeto_sotatsu_uketorinin) { tableSame = false }
    if (t1[i].sotatsu_todokedeto_yubin_bango != t3[i].sotatsu_todokedeto_yubin_bango) { tableSame = false }
    if (t1[i].sotatsu_todokedeto_sotatsu_basho != t3[i].sotatsu_todokedeto_sotatsu_basho) { tableSame = false }
    if (t1[i].hojin_flag != t3[i].hojin_flag) { tableSame = false }
    if (t1[i].daihyosha_shikaku != t3[i].daihyosha_shikaku) { tableSame = false }
    if (t1[i].daihyosha != t3[i].daihyosha) { tableSame = false }
    if (t1[i].biko != t3[i].biko) { tableSame = false }
    if (t1[i].system_kanrenduke_ari != t3[i].system_kanrenduke_ari) { tableSame = false }
    if (t1[i].system_sotatsu_no_todokede != t3[i].system_sotatsu_no_todokede) { tableSame = false }
    if (t1[i].jiken_code != t3[i].jiken_code) { tableSame = false }
    if (t1[i].saibansho_code != t3[i].saibansho_code) { tableSame = false }
    if (t1[i].shinko_kanri_tani != t3[i].shinko_kanri_tani) { tableSame = false }
    if (t1[i].kanren_jiken_code != t3[i].kanren_jiken_code) { tableSame = false }
    if (t1[i].shuyo_basho_code != t3[i].shuyo_basho_code) { tableSame = false }

    let seinengappiSame = true
    if (t1[i].seinengappi && t3[i].seinengappi) {
      seinengappiSame = t1[i].seinengappi.getTime() == t3[i].seinengappi.getTime()
    } else {
      seinengappiSame = t1[i].seinengappi == t3[i].seinengappi
    }
    if (!seinengappiSame) { tableSame = false }

    const m1 = t1[i].hikokunin_jiken_mei_joho
    const m3 = t3[i].hikokunin_jiken_mei_joho

    if (!m1 && !m3) {
      // 둘 다 없으면 같음, 아무것도 안 함
    } else if (!m1 || !m3) {
      tableSame = false
    } else if (m1.length != m3.length) {
      tableSame = false
    } else {
      for (let j = 0; j < m1.length; j++) {
        if (m1[j].zaimei_code != m3[j].zaimei_code) { tableSame = false }
        if (m1[j].zaimei_text != m3[j].zaimei_text) { tableSame = false }
        if (m1[j].moto_zaimei_text != m3[j].moto_zaimei_text) { tableSame = false }
        if (m1[j].henshu_flag != m3[j].henshu_flag) { tableSame = false }
      }
    }

    if (t1[i].gengo != t3[i].gengo) { tableSame = false }
    if (t1[i].seireki != t3[i].seireki) { tableSame = false }
    if (t1[i].month != t3[i].month) { tableSame = false }
    if (t1[i].day != t3[i].day) { tableSame = false }
    if (t1[i].wareki != t3[i].wareki) { tableSame = false }
    if (t1[i].honseki != t3[i].honseki) { tableSame = false }
    if (t1[i].init_gaibu_user_id != t3[i].init_gaibu_user_id) { tableSame = false }
    if (t1[i].daihyosha_jukyo != t3[i].daihyosha_jukyo) { tableSame = false }
    if (t1[i].koryu_seikyu_jiken_code != t3[i].koryu_seikyu_jiken_code) { tableSame = false }
    if (t1[i].koryu_seikyu_jiken_bango != t3[i].koryu_seikyu_jiken_bango) { tableSame = false }
    if (t1[i].shuyo_basho != t3[i].shuyo_basho) { tableSame = false }
    if (t1[i].koryu_saibansho != t3[i].koryu_saibansho) { tableSame = false }
    if (t1[i].kanren_saibansho_code != t3[i].kanren_saibansho_code) { tableSame = false }
    if (t1[i].kanren_shinko_kanri_tani != t3[i].kanren_shinko_kanri_tani) { tableSame = false }
    if (t1[i].kanren_benron_bango != t3[i].kanren_benron_bango) { tableSame = false }
    if (t1[i].kanren_hikokuninto_bango != t3[i].kanren_hikokuninto_bango) { tableSame = false }
    if (t1[i].jiken_bango_kensatsu != t3[i].jiken_bango_kensatsu) { tableSame = false }
  }
}

// jiken_joho 비교 + 테이블 비교 결과 합산
if(input.gengo == varibale.gengo &&
  input.jiken_fugo == varibale.jiken_fugo &&
  input.jiken_renban == varibale.jiken_renban &&
  input.jiken_shubetsu == varibale.jiken_shubetsu &&
  input.kiroku_hensei_flag == varibale.kiroku_hensei_flag &&
  input.moshiokuri_jiko_text == varibale.moshiokuri_jiko_text &&
  input.moshitate_bi.getTime() == varibale.moshitate_bi.getTime() &&
  input.nendo == varibale.nendo &&
  input.renraku_memo == varibale.renraku_memo &&
  input.saiban_hoho == varibale.saiban_hoho &&
  input.saiban_list == varibale.saiban_list &&
  input.saibansho_code == varibale.saibansho_code &&
  input.saibantei_kosei == varibale.saibantei_kosei &&
  input.tantobu == varibale.tantobu &&
  input.tantogakari == varibale.tantogakari &&
  input.uketsuke_kubun == varibale.uketsuke_kubun &&
  tableSame
) {
  console.log("f")
  return false
} else {
  console.log("t")
  return true
}
