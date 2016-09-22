# ActivityBasic02

1. 액티비티사이에 값 주고 받기

  가. 값을 넘길 때
  	// 1. Intent 생성
  	Intent intent = new Intent(this, 대상.class);
  	// 2. 값 세팅
  	intent.putExtra("key1", str);
  	// 3. 액티비티 호출
  	startActivity(intent);

  나. 값을 넘긴 후 돌려 받을 때
  	// 가의 1,2 번 후에 호출
  	startActivityForResult(intent, 다시돌려받을때);
	
  다. 값을 받을 때
  	// 1. 전달받은 인텐트를 가져온다
    Intent intent = getIntent();
    // 2. intent 에서 extra 꾸러미를 꺼낸다
    Bundle bundle = intent.getExtras();
    // 3. 꾸러미에서 key값을 찾아 원하는 값을 꺼낸다
    String str = bundle.getString("key1");
	
  라. 값을 돌려 줄때
	  // 1. 인텐트를 생성하고 돌려줄 값을 세팅한다
    Intent intent = new Intent();
    intent.putExtra("return1", result);
    intent.putExtra("return2", "결과값2");
    // 2. setResult에 결과코드와 데이터를 넘겨준다
    setResult(1, intent);
    // 3. 현재 액티비티 종료
    finish();
	
2. 호출한 액티비티로 부터 값을 돌려받을 때 호출되는 함수
    @Override                           //    ↓ 요청한 버튼을 구별하기 위한 코드 (버튼이 여러개 있을 경우 해당 버튼을 구별하기 위해 사용)
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
         //    호출된 액티비티에서 다시 리턴해주는 결과 코드  ↑ (주로 성공 1, 실패 0 으로 세팅되서 받게된다)
                                                                       //   ↑ 액티비티에서 넘겨준 데이터
        super.onActivityResult(requestCode, resultCode, data);

        // Send 버튼에서 호출할 때 넘겨줬던 코드
        if(requestCode == 0){
            // 호출됬던 액티비티에서 다시 리턴해준 결과 코드
            if(resultCode == 1){
                Bundle bundle = data.getExtras();
                String result = bundle.getString("return1");
                et.setText(result);
            }
        }
    }
