# MyNote
Just some personal notes

//已知两个点,画一条虚线
  // this.sp = new Laya.Sprite();
  // this.addChild(this.sp);
  let p_1 = new Laya.Point(0, 0);//起始点
  let p_2 = new Laya.Point(0, 0);//终点
  p_1.x = this.line.x;
  p_1.y = this.line.y;
  p_2.x = this.aim.x;
  p_2.y = this.aim.y;
  // step1:两点之间的距离
  let len = p_1.distance(p_2.x, p_2.y);
  // //40-- -> 每个线段长40
  if (len > 80) {
     let arr = [];//中间点的数据
     let sum = Math.floor(len / 40);//总共分几段
     //step2:获取线段上的点
     for (let i = 1; i < sum; i++) {
         let x = p_1.x + i * 40 * (p_2.x - p_1.x) / len;//cos--->(p_2.x - p_1.x) / len
         let y = p_1.y + i * 40 * (p_2.y - p_1.y) / len;//sin--->(p_2.y - p_1.y) / len
         arr.push(new Laya.Point(x, y));
     }
     //step3:隔一段绘制一段,这里担心数组越界，就取了总长度减1
     for (let i = 0; i < arr.length - 1; i += 2) {
         this.sp.graphics.drawLine(arr[i].x, arr[i].y, arr[i + 1].x, arr[i + 1].y, "#FFFFFF", 20);
      }
  }
