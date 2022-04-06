这是接入东莞社保的DLL，你要转线后接入东莞社保局局域网后才能使用 由于还在使用，不提供源码，只提供使用办法和DLL编译后的程序在Release

此DLL给还在使用PB，DELPHI VB6 等语言还没有HTTP调用功能语言使用 各变量和开发文档的里各种对应，看Release压缩包的开发文档



        struct general_struct
	{
		const char * accessKey;
		const char * secreKey;
		const char * sbid;
		const char * insuplc_admdvs;
		const char * mdtrtarea_admvs;
		const char * opter_type;
		const char * opter;
		const char * opter_name;
		const char * inf_time;
		const char * fixmedins_code;
		const char * fixmedins_name;
		const char * sign_no;
		int returncode;
		bool iftest;
	}general_struct;
	

	 struct  general_ret_struct {
		char * inf_refmsgid;
		char * refmsg_time;
		char * respond_time;
		char * err_msg;

	}general_ret_struct;


// 【9001】签到

       int   postsignin(general_struct & gs,
		const char * opter_no, const char * netcardname,
		general_ret_struct & grs, char * retsign_time, char * retsign_no);

//6.7.1.2 【9002】签退

	int    postsignout(general_struct & gs,
		const char * opter_no, general_ret_struct & grs, char * retsign_time);


	 struct fsUploadIn_struct{

		const char * path;
		const char * filename;
	}fsUploadIn_struct;

	 struct fsUpload_ret_struct{
		char * file_qury_no;
		char * filename;
		char * fixmedins_code;
		char * dld_endtime;
	}fsUpload_ret_struct;


	int    uploaddgsbfile(general_struct & gs,
		fsUploadIn_struct & fs,
		fsUpload_ret_struct & frs,
		general_ret_struct & grs);

	 struct fsDownloadIn_struct{
		const char * file_qury_no;
		const char * filename;
		const char * fixmedins_code;

	}fsDownloadIn_struct;


	int    downloaddgsbfile(general_struct & gs,
		fsDownloadIn_struct & fs,
		char * plaincstr,
		general_ret_struct & grs);

	 struct clientinfo_struct{
		const char* mdtrt_cert_type;
		const char * mdtrt_cert_no;
		const char * card_sn;
		const char * begntime;
		const char * psn_cert_type;
		const char * certno;
		const char * psn_name;
	}clientinfo_struct;

	 struct clientinfo_baseinfo_ret_struct{
		char * psn_no;
		char * psn_cert_type;
		char * certno;
		char * psn_name;
		char * gend;
		char * naty;
		char * brdy;
		double age;
	}clientinfo_baseinfo_ret_struct;

	 struct clientinfo_insuinfo_ret_struct{
		
		double  balc;
		char * insutype;
		char * psn_type;
		char * psn_insu_stas;
		char * psn_insu_date;
		char * paus_insu_date;
		char * cvlserv_flag;
		char * insuplc_admdvs;
		char * emp_name;

	}clientinfo_insuinfo_ret_struct;

	 struct clientinfo_idetinfo_ret_struct{
	
		char * psn_idet_type;
		char * psn_type_lv;
		char * memo;
		char * begntime;
		char * endtime;
	}clientinfo_idetinfo_ret_struct;


	//1101	人员基本信息获取
	
	int   getclientinfo(general_struct & gs,
		clientinfo_struct & cs,
		clientinfo_baseinfo_ret_struct & cbrs,
		int & insuinforecordscount,
		clientinfo_insuinfo_ret_struct * cinsurs,
		int & idetinforecordscount,
		clientinfo_idetinfo_ret_struct * cidenrs,
		general_ret_struct & grs);

	 struct cal_druginfo_struct{
		const char * psn_no;
		const char * mdtrt_cert_type;
		const char * mdtrt_cert_no;
		const char * begntime;
		double medfee_sumamt;
		const char * insutype;
		const char * dise_codg;
		const char * dise_name;
		const char * acct_used_flag;
		const char * med_type;
	}cal_druginfo_struct;

	 struct cal_drugdetail_struct{
		
		const char * feedetl_sn;
		const char * rxno;
		const char * rx_circ_flag;
		const char * fee_ocur_time;
		const char * med_list_codg;
		const char * medins_list_codg;
		double  det_item_fee_sumamt;
		double  cnt;
		double  pric;
		const char * sin_dos_dscr;
		const char * used_frqu_dscr;
		double  prd_days;
		const char * medc_way_dscr;
		const char * bilg_dr_codg;
		const char * bilg_dr_name;
		const char * tcmdrug_used_way;
	}cal_drugdetail_struct;

	 struct cal_setlinfo_ret_struct{
		char * mdtrt_id;
		char * psn_no;
		char * psn_name;
		char * psn_cert_type;
		char * certno;
		char * gend;
		char * naty;
		char * brdy;
		double  age;
		char * insutype;
		char * psn_type;
		char * cvlserv_flag;
		char * setl_time;
		char * mdtrt_cert_type;
		char * med_type;
		double  medfee_sumamt;
		double  fulamt_ownpay_amt;
		double  overlmt_selfpay;
		double  preselfpay_amt;
		double  inscp_scp_amt;
		double  act_pay_dedc;
		double  hifp_pay;
		double  pool_prop_selfpay;
		double  cvlserv_pay;
		double  hifes_pay;
		double  hifmi_pay;
		double  hifob_pay;
		double  maf_pay;
		double  oth_pay;
		double  fund_pay_sumamt;
		double  psn_part_amt;
		double  acct_pay;
		double  psn_cash_pay;
		double  balc;
		double  acct_mulaid_pay;
		char * medins_setl_id;
		char * clr_optins;
		char * clr_way;
		char * clr_type;
	}cal_setlinfo_ret_struct;

	 struct cal_setldetail_ret_struct{
		
		char * fund_pay_type;
		double  inscp_scp_amt;
		double  crt_payb_lmt_amt;
		double  fund_payamt;
		char * fund_pay_type_name;
		char * setl_proc_info;
	}cal_setldetail_ret_struct;

	 struct cal_detlcutinfo_ret_struct{
	
		char * feedetl_sn;
		double  det_item_fee_sumamt;
		double  cnt;
		double  pric;
		double  pric_uplmt_amt;
		double  selfpay_prop;
		double  fulamt_ownpay_amt;
		double  overlmt_amt;
		double  inscp_scp_amt;
		double  preselfpay_amt;
		char * chrgitm_lv;
		char * med_chrgitm_type;
		char * bas_medn_flag;
		char * hi_nego_drug_flag;
		char * chld_medc_flag;
		char * list_sp_item_flag;
		char * drt_reim_flag;
		char * memo;
	}cal_detlcutinfo_ret_struct;

	//2101	药店预结算
	
	int   postcalthefees(general_struct & gs,
		cal_druginfo_struct & cdis,
		int recordscount,
		cal_drugdetail_struct * cdds,
		cal_setlinfo_ret_struct & csirs,
		int & setldetailrecordscount,
		cal_setldetail_ret_struct * csdrs,
		int  & detlcutinforecordscount,
		cal_detlcutinfo_ret_struct * cdrs,
		general_ret_struct & grs);

	 struct  trans_druginfo_struct {
		const char * psn_no;
		const char * mdtrt_cert_type;
		const char * mdtrt_cert_no;
		const char * begntime;
		double medfee_sumamt;
		const char * invono;
		const char * insutype;
		const char * dise_codg;
		const char * dise_name;
		const char * acct_used_flag;
		const char * med_type;
	} trans_druginfo_struct;

	 struct trans_drugdetail_struct {

		
		const char * feedetl_sn;
		const char * rxno;
		const char * rx_circ_flag;
		const char * fee_ocur_time;
		const char * med_list_codg;
		const char * medins_list_codg;
		double det_item_fee_sumamt;
		double cnt;
		double pric;
		const char * sin_dos_dscr;
		const char * used_frqu_dscr;
		double  prd_days;
		const char * medc_way_dscr;
		const char * bilg_dr_codg;
		const char * bilg_dr_name;
		const char * tcmdrug_used_way;
	} trans_drugdetail_struct;

	 struct trans_ret_setlinfo {

		char * setl_id;
		char * mdtrt_id;
		char * psn_no;
		char * psn_name;
		char * psn_cert_type;
		char * certno;
		char * gend;
		char * naty;
		char * brdy;
		double  age;
		char * insutype;
		char * psn_type;
		char * cvlserv_flag;
		char * setl_time;
		char * mdtrt_cert_type;
		char * med_type;
		double  medfee_sumamt;
		double  fulamt_ownpay_amt;
		double  overlmt_selfpay;
		double  preselfpay_amt;
		double  inscp_scp_amt;
		double  act_pay_dedc;
		double  hifp_pay;
		double  pool_prop_selfpay;
		double  cvlserv_pay;
		double  hifes_pay;
		double  hifmi_pay;
		double  hifob_pay;
		double  maf_pay;
		double  oth_pay;
		double  fund_pay_sumamt;
		double  psn_part_amt;
		double  acct_pay;
		double  psn_cash_pay;
		double  balc;
		double  acct_mulaid_pay;
		char * medins_setl_id;
		char * clr_optins;
		char * clr_way;
		char * clr_type;
	}trans_ret_setlinfo;

	 struct trans_ret_setldetail {
		
		char * fund_pay_type;
		double  inscp_scp_amt;
		double  crt_payb_lmt_amt;
		double  fund_payamt;
		char * fund_pay_type_name;
		char * setl_proc_info;
	}trans_ret_setldetail;

	 struct trans_ret_detlcutinfo {
		
		char * feedetl_sn;
		double  det_item_fee_sumamt;
		double  cnt;
		double  pric;
		double  pric_uplmt_amt;
		double  selfpay_prop;
		double  fulamt_ownpay_amt;
		double  overlmt_amt;
		double  preselfpay_amt;
		double  inscp_scp_amt;
		char * chrgitm_lv;
		char * med_chrgitm_type;
		char * bas_medn_flag;
		char * hi_nego_drug_flag;
		char * chld_medc_flag;
		char * list_sp_item_flag;
		char * drt_reim_flag;
		char * memo;
	}trans_ret_detlcutinfo;


	//2102	药店结算
	
	int   posttransaction(general_struct & gs,
		trans_druginfo_struct & dis,
		int recordscount,
		trans_drugdetail_struct * dds,
		trans_ret_setlinfo & trs,
		int & setldetailrecordscount,
		trans_ret_setldetail * trsd,
		int & detlcutrecordscount,
		trans_ret_detlcutinfo * trd,
		general_ret_struct & grs);


	 struct pullback_struct{
		const char * psn_no;
		const char * setl_id;
		const char * mdtrt_id;

	}pullback_struct;

	 struct pullback_setlinfo_ret_struct{
		char * mdtrt_id;
		char * setl_id;
		char * clr_optins;
		double  medfee_sumamt;
		char * setl_time;
		double  fulamt_ownpay_amt;
		double  overlmt_selfpay;
		double  preselfpay_amt;
		double  inscp_scp_amt;
		double  act_pay_dedc;
		double  hifp_pay;
		double  pool_prop_selfpay;
		double  cvlserv_pay;
		double  hifes_pay;
		double  hifmi_pay;
		double  hifob_pay;
		double  maf_pay;
		double  oth_pay;
		double  fund_pay_sumamt;
		double  psn_pay;
		double  acct_pay;
		double  cash_payamt;
		double  balc;
		double  acct_mulaid_pay;
		char * medins_setl_id;
	}pullback_setlinfo_ret_struct;

	 struct pullback_setldetail_ret_struct{
	
		char * fund_pay_type;
		double  inscp_scp_amt;
		double  crt_payb_lmt_amt;
		double  fund_payamt;
		char * fund_pay_type_name;
		char * setl_proc_info;
	}pullback_setldetail_ret_struct;

	//2103	药店结算撤销
	
	int   pullbacktransaction(general_struct & gs,
		pullback_struct & ps,
		pullback_setlinfo_ret_struct & pslrs,
		int & recordscount,
		pullback_setldetail_ret_struct * psdrs,
		general_ret_struct & grs);

	 struct query_trans_basi_struct{
		const char * psn_no;
		const char * setl_id;
		const char * mdtrt_id;
	}query_trans_basi_struct;

	 struct query_trans_basi_ret_setlinfo{

		char * setl_id;
		char * mdtrt_id;
		char * psn_no;
		char * psn_name;
		char * psn_cert_type;
		char * certno;
		char * gend;
		char * naty;
		char * brdy;
		double age;
		char * insutype;
		char * psn_type;
		char * cvlserv_flag;
		char * flxempe_flag;
		char * nwb_flag;
		char * insu_optins;
		char * emp_name;
		char * pay_loc;
		char * fixmedins_code;
		char * fixmedins_name;
		char * hosp_lv;
		char * fixmedins_poolarea;
		char * lmtpric_hosp_lv;
		char * dedc_hosp_lv;
		char * begndate;
		char * enddate;
		char * setl_time;
		char * mdtrt_cert_type;
		char * med_type;
		char * clr_type;
		char * clr_way;
		char * clr_optins;
		double  medfee_sumamt;
		double  fulamt_ownpay_amt;
		double  overlmt_selfpay;
		double  preselfpay_amt;
		double  inscp_scp_amt;
		double  act_pay_dedc;
		double  hifp_pay;
		double  pool_prop_selfpay;
		double  cvlserv_pay;
		double  hifes_pay;
		double  hifmi_pay;
		double  hifob_pay;
		double  maf_pay;
		double  oth_pay;
		double  fund_pay_sumamt;
		double  psn_pay;
		double  acct_pay;
		double  cash_payamt;
		double  balc;
		double  acct_mulaid_pay;
		char * medins_setl_id;
		char * refd_setl_flag;
		char * year;
		char * dise_codg;
		char * dise_name;
		char * invono;
		char * opter_id;
		char * opter_name;
		char * opt_time;
	}query_trans_basi_ret_setlinfo;

	 struct query_trans_basi_ret_setldetail{
		char * fund_pay_type;
		double  inscp_scp_amt;
		double  crt_payb_lmt_amt;
		double  fund_payamt;
		char * fund_pay_type_name;
		char * setl_proc_info;
	}query_trans_basi_ret_setldetail;


	//5203	结算信息查询
	
	int  querytransbasic(general_struct & gs,
		query_trans_basi_struct & qtbs,
		query_trans_basi_ret_setlinfo & qtbrsl,
		int & recordscount,
		query_trans_basi_ret_setldetail * qtbsd,
		general_ret_struct & grs);

	 struct query_tran_detai_struct{
		const char * psn_no;
		const char *setl_id;
		const char * mdtrt_id;
	}query_tran_detai_struct;

	 struct query_tran_detai_ret_struct{
		char * mdtrt_id;
		char * setl_id;
		char * feedetl_sn;
		char * rx_drord_no;
		char * med_type;
		char * fee_ocur_time;
		double  cnt;
		double  pric;
		char * sin_dos_dscr;
		char * used_frqu_dscr;
		double  prd_days;
		char * medc_way_dscr;
		double  det_item_fee_sumamt;
		double  pric_uplmt_amt;
		double  selfpay_prop;
		double  fulamt_ownpay_amt;
		double  overlmt_amt;
		double  preselfpay_amt;
		double  inscp_scp_amt;
		char * chrgitm_lv;
		char * hilist_code;
		char * hilist_name;
		char * list_type;
		char * med_list_codg;
		char * medins_list_codg;
		char * medins_list_name;
		char * med_chrgitm_type;
		char * prodname;
		char * spec;
		char * dosform_name;
		char * bilg_dept_codg;
		char * bilg_dept_name;
		char * bilg_dr_codg;
		char * bilg_dr_name;
		char * acord_dept_codg;
		char * acord_dept_name;
		char * orders_dr_code;
		char * orders_dr_name;
		char * lmt_used_flag;
		char * hosp_prep_flag;
		char * hosp_appr_flag;
		char * tcmdrug_used_way;
		char * prodplac_type;
		char * bas_medn_flag;
		char * hi_nego_drug_flag;
		char * chld_medc_flag;
		char * etip_flag;
		char * etip_hosp_code;
		char * dscg_tkdrug_flag;
		char * list_sp_item_flag;
		char * matn_fee_flag;
		char * drt_reim_flag;
		char * memo;
		char * opter_id;
		char * opter_name;
		char * opt_time;

	}query_tran_detai_ret_struct;

	//5204	费用明细查询
	
	int   querytransdetail(general_struct & gs,
		query_tran_detai_struct & qtds,
		int & querytrandetairecordscount,
		query_tran_detai_ret_struct * qtdrs,
		general_ret_struct & grs);

	 struct personleverage_struct{
		const char * psn_no;
		const char * insutype;
		const char * fixmedins_code;
		const char * med_type;
		const char * begntime;
		const char * endtime;
		const char * dise_codg;
		const char * dise_name;
		const char * oprn_oprt_code;
		const char * oprn_oprt_name;
		const char * matn_type;
		const char * birctrl_type;

	}personleverage_struct;

	 struct personleverage_ret_struct{
		 
		char * psn_no;
		char * trt_chk_type;
		char * fund_pay_type;
		char * trt_enjymnt_flag;
		char * begndate;
		char * enddate;
		char * trt_chk_rslt;
	}personleverage_ret_struct;

	//2001	人员待遇享受检查
	
	int   getpersonleverage(general_struct & gs,
		personleverage_struct & ps,
		int & recordscount,
		personleverage_ret_struct * prs,
		general_ret_struct & grs);
	
	//2601	冲正交易
	
	int   postcanceloperation(general_struct & gs,
		const char * psn_no, const char * omsgid, const char * oinfno,
		general_ret_struct & grs);

	 struct query_settle_sum_struct{
		const char * insutype;
		const char * clr_type;
		const char * setl_optins;
		const char * stmt_begndate;
		const char * stmt_enddate;
		const char * refd_setl_flag;
		double medfee_sumamt;
		double fund_pay_sumamt;
		double acct_pay;
		int fixmedins_setl_cnt;

	}query_settle_sum_struct;

	 struct query_settle_sum_ret_struct{
		char * setl_optins;
		char * stmt_rslt;
		char * stmt_rslt_dscr;
	}query_settle_sum_ret_struct;


	//3201	医药机构费用结算对总账
	
	int   querytransettlesummary(general_struct & gs,
		query_settle_sum_struct & qsss,
		query_settle_sum_ret_struct & qssrs,
		general_ret_struct & grs);

	 struct query_settle_datail_struct{
		const char * setl_optins;
		const char * stmt_begndate;
		const char * stmt_enddate;
		const char * refd_setl_flag;
		double medfee_sumamt;
		double fund_pay_sumamt;
		double cash_payamt;
		int fixmedins_setl_cnt;
	}query_settle_datail_struct;

	 struct query_file_struct{
		char * file_qury_no;
		char * filename;
		char * fixmedins_code;
		char * dld_endtime;
	}query_file_struct;


	 struct upload_file_content_struct{
		
		const char * setl_id;
		const char * mdtrt_id;
		const char * psn_no;
		double  medfee_sumamt;
		double  fund_pay_sumamt;
		double  acct_pay;
		const char * refd_setl_flag;
	}upload_file_content_struct;

	 struct query_settle_datail_ret_struct{
	
		char * psn_no;
		char * mdtrt_id;
		char * setl_id;
		char * msgid;
		char * stmt_rslt;
		char * refd_setl_flag;
		char * memo;
		char * HICENT_MEDFEE_SUMAMT;
		char * HIF_PAY_SUMAMT;
		char * HICENT_ACCT_PAY;
	}query_settle_datail_ret_struct;


	//3202	医药机构费用结算对明细账
	
	int   querytransettledetail(general_struct & gs,
		query_settle_datail_struct & qsds,
		int updfilerecordscount,
		upload_file_content_struct * updfilecontents,
		fsUpload_ret_struct & updfilestruct,
		query_file_struct & dlfilestruct,
		int & qsdrrecrodscount,
		query_settle_datail_ret_struct * qsdrs,
		general_ret_struct & grs);


	 struct prot_fund_setlinfo_struct{
		const char *   psn_no;
		const char *   mdtrt_id;
		const char *   setl_id;
		const char *   hi_no;
		const char *   medcasno;
		const char *   dcla_time;
		const char *   ntly;
		const char *   prfs;
		const char *   curr_addr;
		const char *   emp_name;
		const char *   emp_addr;
		const char *   emp_tel;
		const char *   poscode;
		const char *   coner_name;
		const char *   patn_rlts;
		const char *   coner_addr;
		const char *   coner_tel;
		const char *   nwb_admtype;
		double  nwbbirwt;
		double  nwbadmwt;
		const char *   mul_nwb_bir_wt;
		const char *   mul_nwb_adm_wt;
		const char *   opsp_diag_caty;
		const char *   opsp_mdtrt_date;
		const char *   adm_way;
		const char *   trt_type;
		const char *   adm_time;
		const char *   refldept_dept;
		const char *   dscg_time;
		const char *   dscg_caty;
		const char *   otp_wm_dise;
		const char *   wm_dise_code;
		const char *   otptcmdise;
		const char *   tcmdisecode;
		const char *   vent_used_dura;
		const char *   pwcry_bfadm_coma_dura;
		const char *   pwcry_afadm_coma_dura;
		int  spga_nurscare_days;
		int  lv1_nurscare_days;
		int  scd_nurscare_days;
		int  lv3_nurscare_days;
		const char *   dscg_way;
		const char *   acp_medins_name;
		const char *   acp_optins_code;
		const char *   bill_code;
		const char *   bill_no;
		const char *   biz_sn;
		const char *   days_rinp_flag_31;
		const char *   days_rinp_pup_31;
		const char *   chfpdr_code;
		const char *   setl_begn_date;
		const char *   setl_end_date;
		const char *   medins_fill_dept;
		const char *   medins_fill_psn;
		const char *   resp_nurs_code;
		const char *   stas_type;
		const char *   hi_paymtd;

	}prot_fund_setlinfo_struct;



	 struct prot_fund_opspdiseinfo{
	
		const char * diag_name;
		const char * diag_code;
		const char * oprn_oprt_name;
		const char * oprn_oprt_code;
	}prot_fund_opspdiseinfo;

	 struct prot_fund_diseinfo{
		
		const char * diag_type;
		const char * diag_code;
		const char * diag_name;
		const char * adm_cond_type;
		const char * maindiag_flag;
	}prot_fund_diseinfo;

 

	 struct prot_fund_oprninfo{
	
		const char *  oprn_oprt_type;
		const char *  oprn_oprt_name;
		const char * oprn_oprt_code;
		const char * anst_way;
	    const char * oper_dr_code;
		const char * anst_dr_code;
		const char * oprn_oprt_begntime;
		const char * oprn_oprt_endtime;
		const char * anst_begntime;
		const char * anst_endtime;
	
	}prot_fund_oprninfo;

	 struct prot_fund_icuinfo{
	 
		const char * scs_cutd_ward_type;
		const char * scs_cutd_inpool_time;
		const char * scs_cutd_exit_time;
		const char * scs_cutd_sum_dura;
	}prot_fund_icuinfo;

	 struct prot_fund_bldinfo {
		const char * bld_cat;
	    int bld_amt;
		const char * bld_unt;

	}prot_fund_bldinfo;

	//4101A	医疗保障基金结算清单信息上传
	
	int   postprotectfundpayinfo2(general_struct & gs,
		prot_fund_setlinfo_struct & pfss,
		int opspdiserecordscount,
		prot_fund_opspdiseinfo * pfopsp,
		int diserecordscount,
		prot_fund_diseinfo * pfd,
	 	int oprnrecordscount,
		prot_fund_oprninfo * pfoi,
		int icurecordscount,
		prot_fund_icuinfo * pfici,
		int bldrecordscount,
		prot_fund_bldinfo * pfbld,
		char * retsetl_list_id,
		general_ret_struct & grs);


	 struct alter_prot_fund_status_struct {
		const char * psn_no;
		const char * setl_id;
		const char * stas_type;
	}alter_prot_fund_status_struct;

	//4102	医疗保障基金结算清单信息状态修改
	
	int  alterprotectfundinfostatus(general_struct & gs,
		int apfsrecordscount,
		alter_prot_fund_status_struct * apfss,
		general_ret_struct & grs);


	 struct query_prot_fund_struct {
		const char * psn_no;
		const char * setl_id;
	}query_prot_fund_struct;

	 struct query_prot_fund_ret_setlinfo {
		char * 	setl_id;
		char * 	setl_list_sn;
		char * 	psn_no;
		char * 	mdtrt_id;
		char * 	fixmedins_name;
		char * 	fixmedins_code;
		char * 	hi_setl_lv;
		char * 	medcasno;
		char * 	dcla_time;
		char * 	psn_name;
		char * 	gend;
		char * 	brdy;
		double	age;
		int	age_days;
		char * 	ntly;
		char * 	naty;
		char * 	psn_cert_type;
		char * 	certno;
		char * 	prfs;
		char * 	curr_addr;
		char * 	emp_name;
		char * 	emp_addr;
		char * 	emp_tel;
		char * 	emp_poscode;
		char * 	coner_name;
		char * 	patn_rlts;
		char * 	coner_addr;
		char * 	coner_tel;
		char * 	insutype;
		char * 	sp_psn_type;
		char * 	insu_admdvs;
		char * 	nwb_adm_type;
		double	nwb_bir_wt;
		double	nwb_adm_wt;
		char * 	mul_nwb_bir_wt;
		char * 	mul_nwb_adm_wt;
		char * 	opsp_diag_caty;
		char * 	opsp_mdtrt_time;
		char * 	ipt_med_type;
		char * 	adm_way_code;
		char * 	trt_type;
		char * 	adm_time;
		char * 	dscg_time;
		char * 	adm_caty;
		char * 	refl_caty;
		char * 	dscg_caty;
		int	act_ipt_days;
		char * 	otp_wm_diag;
		char * 	otp_wm_diag_dise_code;
		char * 	otp_tcm_diag;
		char * 	otp_tcm_diag_dise_code;
		int	diag_code_cnt;
		int	oprn_oprt_code_cnt;
		int	vent_used_days;
		int	vent_used_h_cnt;
		int	vent_used_m_cnt;
		int	bfadm_coma_days;
		int	bfadm_coma_h_cnt;
		int	bfadm_coma_m_cnt;
		int	afadm_coma_days;
		int	afadm_coma_h_cnt;
		int	afadm_coma_m_cnt;
		int	spga_nurscare_days;
		int	lv1_nurscare_days;
		int	scd_nurscare_days;
		int	lv3_nurscare_days;
		char * 	dscg_way;
		char * 	acp_optins_name;
		char * 	acp_optins_code;
		char * 	dscg31days_rinp_flag;
		char * 	rinp_pup;
		char * 	chfpdr_name;
		char * 	chfpdr_code;
		char * 	biz_sn;
		char * 	bill_code;
		char * 	bill_no;
		char * 	setl_begndate;
		char * 	setl_enddate;
		double	psn_selfpay_amt;
		double	psn_ownpay_fee;
		double	acct_payamt;
		double	psn_cashpay;
		char * 	hi_paymtd;
		char * 	medins_fill_dept;
		char * 	medins_fill_psn;
		char * 	hi_no;
		char * 	hi_type;
		char * 	opsp_dise_name;
		char * 	opsp_dise_code;
		char * 	dscg_diag;
		char * 	resp_nurs_name;
		char * 	resp_nurs_code;
		char * 	hsorg_opter_code;
		char * 	stas_type;
		char * 	hsorg_opter_name;
		char * 	hsorg_name;
		char * 	hsorg_code;
		char * 	chk_cont;
	}query_prot_fund_ret_setlinfo;

	 struct query_prot_fund_ret_payinfo {
		char * 	setl_id;
		char * 	psn_no;
		char * 	mdtrt_id;
		char * 	fund_pay_type;
		char * 	poolarea_fund_pay_type;
		char * 	poolarea_fund_pay_name;
		double	fund_payamt;
	}query_prot_fund_ret_payinfo;

	 struct query_prot_fund_ret_opspdiseinfo {
		char * 	setl_list_opsp_trt_id;
		char * 	mdtrt_id;
		char * 	setl_id;
		char * 	psn_no;
		char * 	diag_code;
		char * 	diag_name;
		char * 	oprn_oprt_name;
		char * 	oprn_oprt_code;
	}query_prot_fund_ret_opspdiseinfo;

	 struct query_prot_fund_ret_diseinfo {
		char * 	setl_list_diag_id;
		char * 	setl_id;
		char * 	mdtrt_id;
		char * 	psn_no;
		char * 	diag_type;
		char * 	maindiag_flag;
		char * 	diag_code;
		char * 	diag_name;
		char * 	adm_cond_type;

	}query_prot_fund_ret_diseinfo;

	 struct query_prot_fund_ret_iteminfo {
		char * 	setl_list_chrgitm_id;
		char * 	setl_id;
		char * 	mdtrt_id;
		char * 	psn_no;
		char * 	med_chrgitm_type;
		double 	item_sumamt;
		double 	item_claa_sumfee;
		double 	item_clab_amt;
		double 	item_fulamt_ownpay_amt;
		double 	item_ownpay_amt;
		char * 	sindise_code_name;
		char * 	daysrg_code_name;

	}query_prot_fund_ret_iteminfo;

	 struct query_prot_fund_ret_oprninfo {
		char * 	setl_list_oprn_id;
		char * 	setl_id;
		char * 	psn_no;
		char * 	mdtrt_id;
		char * 	main_oprn_flag;
		char * 	oprn_oprt_name;
		char * 	oprn_oprt_code;
		char * 	oprn_oprt_date;
		char * 	anst_way;
		char * 	oper_dr_name;
		char * 	oper_dr_code;
		char * 	anst_dr_name;
		char * 	anst_dr_code;
		char * 	oprn_oprt_begntime;
		char * 	oprn_oprt_endtime;
		char * 	anst_begntime;
		char * 	anst_endtime;
	}query_prot_fund_ret_oprninfo;

	 struct query_prot_fund_ret_icuinfo {
		char * 	setl_list_scs_cutd_id;
		char * 	psn_no;
		char * 	mdtrt_id;
		char * 	setl_id;
		char * 	scs_cutd_ward_type;
		char * 	scs_cutd_inpool_time;
		char * 	scs_cutd_exit_time;
		char * 	scs_cutd_sum_dura;

	}query_prot_fund_ret_icuinfo;

	 struct query_prot_fund_ret_bldinfo {
		char * 	setl_List_bld_Id;
		char * 	psn_no;
		char * 	mdtrt_id;
		char * 	setl_id;
		char * 	bld_cat;
		int 	bld_amt;
		char * 	bld_unt;
	}query_prot_fund_ret_bldinfo;

	//4103	医疗保障基金结算清单信息查询
	
	int  queryprotectfundrecords(general_struct & gs,
		//query_prot_fund_struct qpfs,
		const char * psno, const char * setlid,
		query_prot_fund_ret_setlinfo & qpfrset,
		int & payrecordscount,
		query_prot_fund_ret_payinfo * qpfrpay,
		int & opspdisrecordscount,
		query_prot_fund_ret_opspdiseinfo * qpfrops,
		int & diserecordscount,
		query_prot_fund_ret_diseinfo * qpfrdis,
		int & itemsrecordscount,
		query_prot_fund_ret_iteminfo * qpfritems,
		int & oprnsrecordscount,
		query_prot_fund_ret_oprninfo * qpfroprns,
		int & icurecrodscount,
		query_prot_fund_ret_icuinfo * qpfricus,
		int & bldrecordscount,
		query_prot_fund_ret_bldinfo * qpfrbld,
		general_ret_struct & grs);


	 struct post_full_pay_feedetail{
		const char * mdtrt_sn;
		const char * ipt_otp_no;
		const char * med_type;
		const char * chrg_bchno;
		const char * feedetl_sn;
		const char * psn_cert_type;
		const char * certno;
		const char * psn_name;
		const char * fee_ocur_time;
		double cnt;
		double pric;
		double det_item_fee_sumamt;
		const char * med_list_codg;
		const char * medins_list_codg;
		const char * medins_list_name;
		const char * med_chrgitm_type;
		const char * prodname;
		const char * bilg_dept_codg;
		const char * bilg_dept_name;
		const char * bilg_dr_codg;
		const char * bilg_dr_name;
		const char * acord_dept_codg;
		const char * acord_dept_name;
		const char * orders_dr_code;
		const char * orders_dr_name;
		const char * tcmdrug_used_way;
		const char * etip_flag;
		const char * etip_hosp_code;
		const char * dscg_tkdrug_flag;
		const char * memo;
	}post_full_pay_feedetail;

	//4201	自费病人费用明细信息上传
	
	int   postfullpayinfo(general_struct & gs,
		post_full_pay_feedetail pfpf,
		general_ret_struct & grs);


	 struct query_consult_struct{
		const char * psn_no;
		const char * begntime;
		const char * endtime;
		const char * med_type;
		const char * mdtrt_id;
	}query_consult_struct;


	 struct query_consult_ret_struct{
		
		char *  mdtrt_id;
		char *  psn_no;
		char *  psn_cert_type;
		char *  certno;
		char *  psn_name;
		char *  gend;
		char *  naty;
		char *  brdy;
		double    age;
		char *  coner_name;
		char *  tel;
		char *  insutype;
		char *  psn_type;
		char *  maf_psn_flag;
		char *  cvlserv_flag;
		char *  flxempe_flag;
		char *  nwb_flag;
		char *  insu_optins;
		char *  emp_name;
		char *  begntime;
		char *  endtime;
		char *  mdtrt_cert_type;
		char *  med_type;
		char *  ars_year_ipt_flag;
		char *  pre_pay_flag;
		char *  ipt_otp_no;
		char *  medrcdno;
		char *  atddr_no;
		char *  chfpdr_name;
		char *  adm_dept_codg;
		char *  adm_dept_name;
		char *  adm_bed;
		char *  dscg_maindiag_code;
		char *  dscg_maindiag_name;
		char *  dscg_dept_codg;
		char *  dscg_dept_name;
		char *  dscg_bed;
		char *  dscg_way;
		char *  main_cond_dscr;
		char *  dise_codg;
		char *  dise_name;
		char *  oprn_oprt_code;
		char *  oprn_oprt_name;
		char *  otp_diag_info;
		char *  inhosp_stas;
		char *  die_date;
		int     ipt_days;
		char *  fpsc_no;
		char *  matn_type;
		char *  birctrl_type;
		char *  latechb_flag;
		int    geso_val;
		int    fetts;
		int    fetus_cnt;
		char *  pret_flag;
		char *  birctrl_matn_date;
		char *  cop_flag;
		char *  opter_id;
		char *  opter_name;
		char *  opt_time;
		char *  memo;
	}query_consult_ret_struct;

	//5201	就诊信息查询
	
	int   queryconsultrecrods(general_struct & gs,
		query_consult_struct & qcs,
		int & recordscount,
		query_consult_ret_struct * qcrs,
		general_ret_struct & grs);

	 struct query_disea_ret_struct{
	
		char *  diag_info_id;
		char *  mdtrt_id;
		char *  psn_no;
		char *  inout_diag_type;
		char *  diag_type;
		char *  maindiag_flag;
		int   diag_srt_no;
		char *  diag_code;
		char *  diag_name;
		char *  adm_cond;
		char *  diag_dept;
		char *  dise_dor_no;
		char *  dise_dor_name;
		char *  diag_time;
		char *  opter_id;
		char *  opter_name;
		char *  opt_time;
	}query_disea_ret_struct;

	//5202	诊断信息查询
	
	int   querydiseaserecords(general_struct & gs,
		const char * mdtrt_id, const char * psn_no,
		int  & recordscount,
		query_disea_ret_struct * qdrs,
		general_ret_struct & grs);


	 struct query_chronic_struct{
		const char * psn_no;
		const char * begntime;
		const char * endtime;
	}query_chronic_struct;


	 struct query_chronic_ret_struct{
		char * feedetl_sn;
		char * rx_drord_no;
		char * fixmedins_code;
		char * fixmedins_name;
		char * psn_no;
		char * med_type;
		char * fee_ocur_time;
		double  cnt;
		double  pric;
		char * chrgitm_lv;
		char * hilist_code;
		char * hilist_name;
		char * list_type;
		char * med_list_codg;
		char * medins_list_codg;
		char * medins_list_name;
		char * med_chrgitm_type;
		char * prodname;
		char * spec;
		char * dosform_name;
		char * lmt_used_flag;
		char * hosp_prep_flag;
		char * hosp_appr_flag;
		char * tcmdrug_used_way;
		char * prodplac_type;
		char * bas_medn_flag;
		char * hi_nego_drug_flag;
		char * chld_medc_flag;
		char * etip_flag;
		char * etip_hosp_code;
		char * dscg_tkdrug_flag;
		char * list_sp_item_flag;
		char * matn_fee_flag;
	
	}query_chronic_ret_struct;

	//5205	人员慢特病用药记录查询
	
	int   querychronicrecords(general_struct & gs,
		query_chronic_struct & qcs,
		int & recordscount,
		query_chronic_ret_struct * qcrs,
		general_ret_struct & grs);


	 struct query_personal_med{
	
		char * opsp_dise_code;
		char *  opsp_dise_name;
		char *  begndate;
		char *  enddate;
	}query_personal_med;

	//5301	人员慢特病备案查询
	
	int   querypersonalmedrecords(general_struct & gs,
		const char * psn_no,
		int & recordscount,
		query_personal_med * qpm,
		general_ret_struct & grs);

	 struct dl_ret_struct{
		char * file_qury_no;
		char * filename;
		char * dld_end_time;
		int  datalength;
	}dl_ret_struct;

	 struct dl_content_struct{
		char * contents;
	}dl_content_struct;

	//1301	西药中成药目录下载
	
	int   dlpharmdict(general_struct & gs,
		const char * ver,
		dl_ret_struct & drs,
		dl_content_struct & dcs,
		general_ret_struct & grs);

	//1302	中药饮片目录下载
	
	int   dlchinesetraditiondict(general_struct & gs,
		const char * ver,
		dl_ret_struct & drs,
		dl_content_struct & dcs,
		general_ret_struct & grs);


	//1309	门诊慢特病种目录下载
	
	int   dlchonicdict(general_struct & gs,
		const char * ver,
		dl_ret_struct & drs,
		dl_content_struct & dcs,
		general_ret_struct & grs);

	 struct query_insur_prod_struct{
		const char * query_date;
		const char * hilist_code;
		const char * insu_admdvs;
		const char * begndate;
		const char * hilist_name;
		const char * wubi;
		const char * pinyin;
		const char * med_chrgitm_type;
		const char * chrgitm_lv;
		const char * lmt_used_flag;
		const char * list_type;
		const char * med_use_flag;
		const char * matn_used_flag;
		const char * hilist_use_type;
		const char * lmt_cpnd_type;
		const char * vali_flag;
		const char * updt_time;
		int page_num;
		int page_size;
	}query_insur_prod_struct;

	 struct query_insur_prod_ret_struct{
		
		char *  hilist_code;
		char *  hilist_name;
		char *  insu_admdvs;
		char *  begndate;
		char *  enddate;
		char *  med_chrgitm_type;
		char *  chrgitm_lv;
		char *  lmt_used_flag;
		char *  list_type;
		char *  med_use_flag;
		char *  matn_used_flag;
		char *  hilist_use_type;
		char *  lmt_cpnd_type;
		char *  wubi;
		char *  pinyin;
		char *  memo;
		char *  vali_flag;
		char *  rid;
		char *  updt_time;
		char *  crter_id;
		char *  crter_name;
		char *  crte_time;
		char *  crte_optins_no;
		char *  opter_id;
		char *  opter_name;
		char *  opt_time;
		char *  optins_no;
		char *  poolarea_no;
		

	}query_insur_prod_ret_struct;


	//1312	医保目录信息下载
	
	int   queryinsuranceprod(general_struct & gs,
		query_insur_prod_struct & qips,
		int  & recordscount,
		query_insur_prod_ret_struct * qiprs,
		int & totalrecordscount,
	    int &  totalpages,
		general_ret_struct & grs);


	 struct query_insur_relationship_struct{
		const char * query_date;
		const char * medins_list_codg;
		const char * hilist_code;
		const char * list_type;
		const char * insu_admdvs;
		const char * begndate;
		const char * vali_flag;
		const char * updt_time;
		int page_num;
		int page_size;
	}query_insur_relationship_struct;

	 struct query_insur_relat_ret_struct{
		
		char * med_list_codg;
		char * hilist_code;
		char * list_type;
		char * insu_admdvs;
		char * begndate;
		char * enddate;
		char * memo;
		char * vali_flag;
		char * rid;
		char * updt_time;
		char * crter_id;
		char * crter_name;
		char * crte_time;
		char * crte_optins_no;
		char * opter_id;
		char * opter_name;
		int  opt_time;
		char * optins_no;
		char * poolarea_no;
	
	}query_insur_relat_ret_struct;


	//1316	医疗目录与医保目录匹配信息下载
	
	int   queryinsurelation(general_struct & gs,
		query_insur_relationship_struct & qirs,
		int  & recordscount,
		query_insur_relat_ret_struct * qirrs,
		int  & totalrecordscount,
	      int & totalpages,
		general_ret_struct & grs);


	 struct query_prod_relat_struct{
		const char * query_date;
		const char * fixmedins_code;
		const char * medins_list_codg;
		const char * medins_list_name;
		const char * insu_admdvs;
		const char * list_type;
		const char * med_list_codg;
		const char * begndate;
		const char * vali_flag;
		const char * updt_time;
		int page_num;
		int page_size;
	}query_prod_relat_struct;

	 struct query_prod_relat_ret_struct{
		
		char * fixmedins_code;
		char * medins_list_codg;
		char * medins_list_name;
		char * insu_admdvs;
		char * list_type;
		char * med_list_codg;
		char * begndate;
		char * enddate;
		char * aprvno;
		char * dosform;
		char * exct_cont;
		char * item_cont;
		char * prcunt;
		char * spec;
		char * pacspec;
		char * memo;
		char * vali_flag;
		char * rid;
		char * updt_time;
		char * crter_id;
		char * crter_name;
		char * crte_time;
		char * crte_optins_no;
		char * opter_id;
		char * opter_name;
		char * opt_time;
		char * optins_no;
		char * poolarea_no;
	
	}query_prod_relat_ret_struct;

	//1317	医药机构目录匹配信息下载
	
	int   queryprodlocalninusrancrelation(general_struct & gs,
		query_prod_relat_struct & qprs,
		int &  recordscount,
		query_prod_relat_ret_struct * qprrs,
		int &   totalrecordscount,
		int   & totalpages,
		general_ret_struct & grs);

	 struct query_restr_pric_struct{
		const char * query_date;
		const char * hilist_code;
		const char * hilist_lmtpric_type;
		const char * overlmt_dspo_way;
		const char * insu_admdvs;
		const char * begndate;
		const char * enddate;
		const char * vali_flag;
		const char * rid;
		const char * tabname;
		const char * poolarea_no;
		const char * updt_time;
		int page_num;
		int page_size;
	}query_restr_pric_struct;

	 struct query_restr_pric_ret_struct{
		
		char * hilist_code;
		char * hilist_lmtpric_type;
		char * overlmt_dspo_way;
		char * insu_admdvs;
		char * begndate;
		char * enddate;
		double   hilist_pric_uplmt_amt;
		char * vali_flag;
		char * rid;
		char * updt_time;
		char * crter_id;
		char * crter_name;
		char * crte_time;
		char * crte_optins_no;
		char * opter_id;
		char * opter_name;
		char * opt_time;
		char * optins_no;
		char * tabname;
		char * poolarea_no;
		
	}query_restr_pric_ret_struct;

	//1318	医保目录限价信息下载
	
	int   queryretrictedpriceprod(general_struct & gs,
		query_restr_pric_struct & qrps,
		int & recordscount,
		query_restr_pric_ret_struct * qrprs,
		int & totalrecordscount,
		int & totalpages,
		general_ret_struct & grs);

	 struct query_own_pay_per_struct{
		const char * query_date;
		const char * hilist_code;
		const char * selfpay_prop_psn_type;
		const char * selfpay_prop_type;
		const char * insu_admdvs;
		const char * begndate;
		const char * enddate;
		const char * vali_flag;
		const char * rid;
		const char * tabname;
		const char * poolarea_no;
		const char * updt_time;
		int page_num;
		int page_size;
	} query_own_pay_per_struct;

	 struct query_own_pay_per_ret_struct{
		
		char * hilist_code;
		char * selfpay_prop_psn_type;
		char * selfpay_prop_type;
		char * insu_admdvs;
		char * begndate;
		char * enddate;
		char * selfpay_prop;
		char * vali_flag;
		char * rid;
		char * updt_time;
		char * crter_id;
		char * crter_name;
		char * crte_time;
		char * crte_optins_no;
		char * opter_id;
		char * opter_name;
		char * opt_time;
		char * optins_no;
		char * tabname;
		char * poolarea_no;
		
	} query_own_pay_per_ret_struct;

	//1319	医保目录先自付比例信息下载
	
	int   queryownexpenseper(general_struct & gs,
		query_own_pay_per_struct & qopps,
		int  & recordscount,
		query_own_pay_per_ret_struct * qoprs,
		int &   totalrecordscount,
	    int  & totalpages,
		general_ret_struct & grs);

	 struct query_dict_struct{
		const char * type;
		const char * parentValue;
		const char * admdvs;
		const char * date;
		const char * valiFlag;
	}query_dict_struct;

	 struct query_dict_ret_struct{
		
		char * type;
		char * label;
		char * value;
		char * parentValue;
		int  sort;
		char * valiFlag;
		char * createUser;
		char * createDate;
		int  version;
	}query_dict_ret_struct;


	//1901	字典表下载
	
	int   querydict(general_struct & gs,
		query_dict_struct & qds,
		int  & recordscount,
		query_dict_ret_struct * qdrs,
		general_ret_struct & grs);

	 struct query_psn_info_struct{
		const char * psn_no;
		const char * biz_appy_type;
	}query_psn_info_struct;

	 struct query_psn_info_ret_struct{
	
		char * psn_no;
		char * insutype;
		char * fix_srt_no;
		char * fixmedins_code;
		char * fixmedins_name;
		char * begndate;
		char * enddate;
		char *  memo;

	}query_psn_info_ret_struct;


	//5302 人员定点信息查询
	
	int   querypsninfo(general_struct & gs,
		query_psn_info_struct & qpis,
		int & retrecordscount,
		query_psn_info_ret_struct * qpirs,
		general_ret_struct & grs);

	 struct post_conslutreg_struct{
		const char * psn_no;
		const char * insutype;
		const char * begntime;
		const char * mdtrt_cert_type;
		const char * mdtrt_cert_no;
		const char * ipt_otp_no;
		const char * atddr_no;
		const char * dr_name;
		const char * dept_code;
		const char * dept_name;
		const char * caty;

	}post_conslutreg_struct;

	 struct post_conslutreg_ret_struct{
		char * mdtrt_id;
		char * psn_no;
		char * ipt_otp_no;

	}post_conslutreg_ret_struct;


	//2201 门诊挂号
	
	int   postconslutreg(general_struct & gs,
		post_conslutreg_struct & pcs,
		post_conslutreg_ret_struct & pcrs,
		general_ret_struct & grs);

	 struct post_mdtrtinfo_struct{
		const char * mdtrt_id;
		const char * psn_no;
		const char * med_type;
		const char * begntime;
		const char * main_cond_dscr;
		const char * dise_codg;
		const char * dise_name;
		const char * birctrl_type;
		const char * birctrl_matn_date;


	}post_mdtrtinfo_struct;

	 struct post_diseinfo_struct{
	 
		const char * diag_type;
		int  diag_srt_no;
		const char * diag_code;
		const char * diag_name;
		const char * diag_dept;
		const char * dise_dor_no;
		const char * dise_dor_name;
		const char * diag_time;
		const char * vali_flag;
	}post_diseinfo_struct;


	//2203 门诊就诊信息上传
	
	int   postconslutinfo(general_struct & gs,
		post_mdtrtinfo_struct & pmis,
		int recordscount,
		post_diseinfo_struct *  pdis,
		general_ret_struct & grs);


	 struct post_clinic_detail_struct{
		 
		const char* feedetl_sn;
		const char * mdtrt_id;
		const char * psn_no;
		const char * chrg_bchno;
		const char * dise_codg;
		const char * rxno;
		const char * rx_circ_flag;
		const char * fee_ocur_time;
		const char * med_list_codg;
		const char * medins_list_codg;
		double  det_item_fee_sumamt;
		double  cnt;
		double  pric;
		const char * sin_dos_dscr;
		const char * used_frqu_dscr;
		double  prd_days;
		const char * medc_way_dscr;
		const char * bilg_dept_codg;
		const char * bilg_dept_name;
		const char * bilg_dr_codg;
		const char * bilg_dr_name;
		const char * acord_dept_codg;
		const char * acord_dept_name;
		const char * orders_dr_code;
		const char * orders_dr_name;
		const char * hosp_appr_flag;
		const char * tcmdrug_used_way;
		const char * etip_flag;
		const char * etip_hosp_code;
		const char * dscg_tkdrug_flag;
		const char * matn_fee_flag;

	}post_clinic_detail_struct;

	 struct post_clinic_detail_ret_struct{
	 
		char * feedetl_sn;
		double  det_item_fee_sumamt;
		double  cnt;
		double  pric;
		double  pric_uplmt_amt;
		double  selfpay_prop;
		double  fulamt_ownpay_amt;
		double  overlmt_amt;
		double  preselfpay_amt;
		double  inscp_scp_amt;
		char *	 chrgitm_lv;
		char *	 med_chrgitm_type;
		char *	 bas_medn_flag;
		char *	 hi_nego_drug_flag;
		char *	 chld_medc_flag;
		char *	 list_sp_item_flag;
		char *	 lmt_used_flag;
		char *   drt_reim_flag;
		char *	 memo;


	}post_clinic_detail_ret_struct;

	//2204 门诊费用明细信息上传
	
	int   postclinicdetail(general_struct & gs,
		int post_clinic_details_count,
		post_clinic_detail_struct * pcds,
		int & post_clinic_detail_ret_recordscount,
		post_clinic_detail_ret_struct * pcdrs,
		general_ret_struct & grs);

	 struct cal_clinic_fees_struct{
		const char * psn_no;
		const char * mdtrt_cert_type;
		const char * mdtrt_cert_no;
		const char * med_type;
		double medfee_sumamt;
		const char * psn_setlway;
		const char * mdtrt_id;
		const char * chrg_bchno;
		const char * acct_used_flag;
		const char * insutype;


	}cal_clinic_fees_struct;

	 struct cal_clinic_fess_ret_setlinfo{

		char * mdtrt_id;
		char * psn_no;
		char * psn_name;
		char * psn_cert_type;
		char * certno;
		char * gend;
		char * naty;
		char * brdy;
		double age;
		char * insutype;
		char * psn_type;
		char * cvlserv_flag;
		char * setl_time;
		char * mdtrt_cert_type;
		char * med_type;
		double medfee_sumamt;
		double fulamt_ownpay_amt;
		double overlmt_selfpay;
		double preselfpay_amt;
		double inscp_scp_amt;
		double act_pay_dedc;
		double hifp_pay;
		double pool_prop_selfpay;
		double cvlserv_pay;
		double hifes_pay;
		double hifmi_pay;
		double hifob_pay;
		double maf_pay;
		double oth_pay;
		double fund_pay_sumamt;
		double psn_part_amt;
		double acct_pay;
		double psn_cash_pay;
		double hosp_part_amt;
		double balc;
		double acct_mulaid_pay;
		char * medins_setl_id;
		char * clr_optins;
		char * clr_way;
		char * clr_type;


	} cal_clinic_fess_ret_setlinfo;

	 struct cal_clinic_fees_ret_setldetail{
		
		char * fund_pay_type;
		double  inscp_scp_amt;
		double  crt_payb_lmt_amt;
		double  fund_payamt;
		char * fund_pay_type_name;
		char * setl_proc_info;

	}cal_clinic_fees_ret_setldetail;

	//2206 门诊预结算
	
	int   calclinicfees(general_struct & gs,
		cal_clinic_fees_struct & ccfs,
		cal_clinic_fess_ret_setlinfo & ccfrsl,
		int & recordscount,
		cal_clinic_fees_ret_setldetail * ccfrsd,
		general_ret_struct & grs);

	 struct post_clinic_tran_struct{
		const char * psn_no;
		const char *mdtrt_cert_type;
		const char *mdtrt_cert_no;
		const char *med_type;
		double medfee_sumamt;
		const char *psn_setlway;
		const char *mdtrt_id;
		const char *chrg_bchno;
		const char *insutype;
		const char *acct_used_flag;
		const char *invono;
		double fulamt_ownpay_amt;
		double overlmt_selfpay;
		double  preselfpay_amt;
		double  inscp_scp_amt;

	}post_clinic_tran_struct;

	 struct post_clinic_trans_ret_setlinfo{

		char * mdtrt_id;
		char * setl_id;
		char * psn_no;
		char * psn_name;
		char * psn_cert_type;
		char * certno;
		char * gend;
		char * naty;
		char * brdy;
		double age;
		char * insutype;
		char * psn_type;
		char * cvlserv_flag;
		char * setl_time;
		char * mdtrt_cert_type;
		char * med_type;
		double medfee_sumamt;
		double fulamt_ownpay_amt;
		double overlmt_selfpay;
		double preselfpay_amt;
		double inscp_scp_amt;
		double act_pay_dedc;
		double hifp_pay;
		double pool_prop_selfpay;
		double cvlserv_pay;
		double hifes_pay;
		double hifmi_pay;
		double hifob_pay;
		double maf_pay;
		double oth_pay;
		double fund_pay_sumamt;
		double psn_part_amt;
		double acct_pay;
		double psn_cash_pay;
		double hosp_part_amt;
		double balc;
		double acct_mulaid_pay;
		char * medins_setl_id;
		char * clr_optins;
		char * clr_way;
		char * clr_type;

	} post_clinic_trans_ret_setlinfo;


	 struct post_clinic_trans_ret_setldetail{
		
		char * fund_pay_type;
		double  inscp_scp_amt;
		double  crt_payb_lmt_amt;
		double  fund_payamt;
		char * fund_pay_type_name;
		char * setl_proc_info;

	}post_clinic_trans_ret_setldetail;

	//2207 门诊结算
	
	int   postclinictrans(general_struct & gs,
		post_clinic_tran_struct & pcts,
		post_clinic_trans_ret_setlinfo & pctrsl,
		int & pcdretrecordscount,
		post_clinic_trans_ret_setldetail * pctrsd,
		general_ret_struct & grs);

	 struct pullback_clinic_trans_struct{
		const char * setl_id;
		const char *mdtrt_id;
		const char *psn_no;

	}pullback_clinic_trans_struct;


	 struct pullback_clinic_trans_ret_setlinfo{
		char * mdtrt_id;
		char * setl_id;
		char * clr_optins;
		char * setl_time;
		double medfee_sumamt;
		double fulamt_ownpay_amt;
		double overlmt_selfpay;
		double preselfpay_amt;
		double inscp_scp_amt;
		double act_pay_dedc;
		double hifp_pay;
		double pool_prop_selfpay;
		double cvlserv_pay;
		double hifes_pay;
		double hifmi_pay;
		double hifob_pay;
		double maf_pay;
		double oth_pay;
		double fund_pay_sumamt;
		double psn_part_amt;
		double acct_pay;
		double balc;
		double acct_mulaid_pay;
		double hosp_part_amt;
		char * medins_setl_id;
		double pdn_cash_pay;
	}pullback_clinic_trans_ret_setlinfo;


	 struct pullback_clinic_trans_ret_setldetail{
		
		char * fund_pay_type;
		double  inscp_scp_amt;
		double  crt_payb_lmt_amt;
		double  fund_payamt;
		char * fund_pay_type_name;
		char * setl_proc_info;

	}pullback_clinic_trans_ret_setldetail;


	//2208 门诊结算撤销
	
	int   pullbackclinictrans(general_struct & gs,
		pullback_clinic_trans_struct & ccts,
		pullback_clinic_trans_ret_setlinfo cctrsl,
		int & recordscount,
		pullback_clinic_trans_ret_setldetail * cctrsd,
		general_ret_struct & grs);


	//2205 门诊费用明细信息撤销
	
	int   cancelclinicdetail(general_struct & gs,
		const char * mdtrt_id,
		const char *chrg_bchno,
		const char * psn_no,
		general_ret_struct & grs);

	//2202 门诊挂号撤销
	
	int    cancelclinicreg(general_struct & gs,
		const char * psn_no,
		const char *mdtrt_id,
		const char * ipt_otp_no,
		general_ret_struct & grs);

	 struct query_hosp_info_struct {
		const char * fixmedins_type;
		const char * fixmedins_name;
		const char * fixmedins_code;

	}query_hosp_info_struct;

	 struct query_hosp_info_ret_struct {
		char * fixmedins_code;
		char *	fixmedins_name;
		char *	uscc;
		char *	fixmedins_type;
		char *	hosp_lv;

	}query_hosp_info_ret_struct;

	//1201 医药机构信息获取
	
	int  queryhospinfo(general_struct & gs,
		query_hosp_info_struct & qhis,
		int &  recordscount,
		query_hosp_info_ret_struct & qhirs,
		general_ret_struct & grs);

	 struct settel_monthly_struct {
		const char *  setl_time;
		const char *  insutype;
		const char * clr_type;
		const char *  med_type;
		int	pageNum;
	}settel_monthly_struct;

	 struct settel_monthly_ret_struct {
		int totalRow;
		int totalPage;
	}settel_monthly_ret_struct;

	 struct settel_monthly_ret_setlinfo_struct {
		double 	seqno;
		char * 	setl_id;
		char * 	mdtrt_id;
		char * 	psn_no;
		char * 	psn_name;
		char * 	psn_cert_type;
		char * 	certno;
		char * 	gend;
		char * 	naty;
		char * 	brdy;
		double 	age;
		char * 	insutype;
		char * 	psn_type;
		char * 	cvlserv_flag;
		char * 	flxempe_flag;
		char * 	nwb_flag;
		char * 	insu_optins;
		char * 	emp_name;
		char * 	fixmedins_code;
		char * 	fixmedins_name;
		char * 	hosp_lv;
		char * 	fix_blng_admdvs;
		char * 	begndate;
		char * 	enddate;
		char * 	setl_time;
		char * 	med_type;
		char * 	clr_type;
		char * 	clr_way;
		char * 	clr_optins;
		char * 	clr_type_lv2;
		double 	medfee_sumamt;
		double 	fulamt_ownpay_amt;
		double 	overlmt_selfpay;
		double 	preselfpay_amt;
		double 	inscp_amt;
		double 	act_pay_dedc;
		double 	fund_pay_sumamt;
		double 	psn_pay;
		double 	acct_pay;
		double 	cash_payamt;
		double 	balc;
		double 	acct_mulaid_pay;
		char * 	year;
		char * 	dise_no;
		char * 	dise_name;
		char * 	medins_stmt_flag;
		char * 	refd_setl_flag;
		char * 	clr_flag;
		char * 	ide_admdvs;
		char * 	pay_loc;
		char * 	invono;
		double 	hifp_pay;
		double 	cvlserv_pay;
		double 	hifes_pay;
		double 	hifmi_pay;
		double 	hifob_pay;
		double 	hifdm_pay;
		double 	maf_pay;
		double 	othfund_pay;

	}settel_monthly_ret_setlinfo_struct;

	 struct settel_monthly_ret_setldetail_struct {

		char * 	setl_id;
		char * 	mdtrt_id;
		char * 	fund_pay_type;
		char * 	poolarea_fund_pay_type;
		double 	fund_payamt;

	}settel_monthly_ret_setldetail_struct;
	

	//90502 月结对数
	
  int  settelmonthly(general_struct & gs,
		settel_monthly_struct  & smstr ,
		settel_monthly_ret_struct & smrs,
		int &  setlinforecordscount,
		settel_monthly_ret_setlinfo_struct * smrss,
		int & setldetailrecordscount,
		settel_monthly_ret_setldetail_struct * smrsds,
		general_ret_struct & grs);


	 struct query_settle_monthly_struct {
		const char * cashym;
		const char * clr_type;
		const char * clr_type_lv2;
     }query_settle_monthly_struct;

	 struct query_settle_monthly_ret_setlinfo {
		char * 	clr_appy_evt_id;
		char * 	fee_clr_id;
		char * 	fixmedins_name;
		char * 	fixmedins_code;
		char * 	cashym;
		char * 	insutype;
		char * 	clr_stas;
		char * 	clr_ym;
		char * 	clr_type;
		char * 	clr_type_lv2;
		double 	clr_psntime;
		char * 	begndate;
		char * 	enddate;
		double 	medfee_sumamt;
		double 	fund_appy_sum;
		double 	dfr_amt;
		double 	det_sumamt;
		double 	act_dfr_amt;
		double 	dpst_sumamt;
		double 	cash_payamt;
		double 	acct_pay;
		double 	jzsqjy;
		double 	jzsyjy;
		double 	jzxqsyje;
		double 	ljcz;
		double 	yjsed;
		double 	dqkyed;
		double 	sbjzje;
		double 	yljz;
		double 	yfbz;
		double 	cznrdqhz;
		double 	jgbz;
		double 	ylzgdxje;
		double 	yljjsjs;
		double 	iptdayscum;
		double 	zfrc;
		double 	rcbfje;
		char * 	qsnd;
	}query_settle_monthly_ret_setlinfo;

	 struct query_settle_monthly_ret_setldetail {
       
		char *  fee_clr_id;
		char *	fund_pay_type;
		char *	poolarea_fund_pay_type;
		double	fund_appy_sum;
		double	dpst;
		double	det_sumamt;
		double	act_dfr_amt;

     }query_settle_monthly_ret_setldetail;


	//90504 月结信息查询
  
	int  querysettelmonthly(general_struct & gs,
		query_settle_monthly_struct & qsms,
		int &  setlinforecordscount,
		query_settle_monthly_ret_setlinfo * qsmrset,
		int & setldetailrecordscount,
		query_settle_monthly_ret_setldetail * qsmrsdetail,
		general_ret_struct & grs);
