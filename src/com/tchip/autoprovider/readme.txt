Name				Value		Description
--------------------------------------------
rec_back_state		0,1			��¼¼��״̬
rec_front_state		0,1			ǰ¼¼��״̬
rec_front_size		720,1080	ǰ¼�ֱ���
rec_front_time		1,3			ǰ¼�ֶ�

weather_loc_city	����			������λ����
weather_loc_time				������λʱ��
weather_info		��			������Ϣ
weather_temp_low	15			�����������
weather_temp_high	25			�����������

music_play_state	0,1			���ֲ���״̬
music_play_name					���ڲ��Ÿ�����

bt_music_state		0,1			������������״̬

fm_transmit_state	0,1			FM����״̬
fm_transmit_freq				FM����Ƶ��

edog_power_state	0,1			���ӹ���Դ״̬

set_auto_light_state	0,1		�Զ����ȿ���
set_detect_crash_state	0,1		��ײ��⿪��
set_detect_crash_level	1,2,3	��ײ���������(��,��,��)
set_park_monitor_state	0,1		ͣ����������
--------------------------------------------
			Uri uri = Uri.parse("content://com.tchip.provider.AutoProvider/state/name/"
							+ name);
			ContentResolver resolve = context.getContentResolver();
			Cursor cursor = resolve.query(uri, null, null, null, null);
			if (cursor.getCount() > 0) {
				cursor.moveToFirst();
				videoLock = cursor.getInt(cursor.getColumnIndex("lock"));
				cursor.close();
			} else {
				videoLock = 0;
			}

			if (1 == videoLock) {
				isFileLock = true;
			}
