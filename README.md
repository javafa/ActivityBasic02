# ActivityBasic02

1. 액티비티사이에 값 주고 받기

  가. 값을 넘길 때
  
  startActivity(intent);

  나. 값을 넘긴 후 돌려 받을 때

  startActivityForResult(intent, 다시돌려받을때);
	
  다. 값을 받을 때
  
  Intent intent = getIntent();
  Bundle bundle = intent.getExtras();
  String str = bundle.getString("key1");
	
  라. 값을 돌려 줄때
    setResult(1, intent);

2. 호출한 액티비티로 부터 값을 돌려받을 때 호출되는 함수
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
    }
