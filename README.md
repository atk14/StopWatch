StopWatch
=========

A PHP class for precise time measurement.

Basic usage
-----------

    $s = new StopWatch();

    $s->start();
    // do something...
    $s->stop(); 

    // printing result
    echo $s->getResult(); // (float) 3.6618700027466
    // or
    echo $s; // to string conversion provides humanized output, e.g. "0:03.662"


Usual usage
-----------

    $s = new StopWatch();

    $s->start("total");

      $s->start("parsing_request");
      // do something
      $s->stop("parsing_request");

      $s->start("preparing_data");
      // do something
      $s->stop("preparing_data");

      $s->start("rendering");
      
        // do something

        $s->start("rendering_partial_template");
        // do something
        $s->stop("rendering_partial_template");

        $s->start("rendering_partial_template");
        // do something
        $s->stop("rendering_partial_template");

      $s->stop("rendering");

    $s->stop("total");

Print results

    echo $s->getResult("total"); // 0.034516096115112
    echo $s->getResult("rendering"); // 0.017526865005493

For overal report there is a special method

    echo $s->getPrintableOutput();

The output is pretty cool :)

                         total:  0.034516
               parsing_request:  0.004428
                preparing_data:  0.003821
                     rendering:  0.017527
    rendering_partial_template:  0.003695
    rendering_partial_template:  0.003743
              ----------------: total
                         total x 1:    0.0345s
               parsing_request x 1:    0.0044s
                preparing_data x 1:    0.0038s
                     rendering x 1:    0.0175s
    rendering_partial_template x 2:    0.0074s
